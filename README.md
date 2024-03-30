# skos-vocabulary-template
A template for new OpenActive SKOS Vocabulary repositories.

## Use

In order to create a new OpenActive SKOS Vocabulary please follow this guide:

Note that when this template is used, this section of the README should be removed, and the content below adapted according for the new vocabulary.

## Contribution

### Architecture

The workflows that drive SKOS Vocabulary publishing are dependent on the `skos-vocabulary-workflows`, which in turn depends on `skos-vocabulary-editor`, `skos-compare-action` and `SKOS.js` repositories.

Note that any changes made to this repository will only impact new SKOS Vocabularies. Any changes made here must be applied to each existing SKOS Vocabulary. This repository is therefore intentional minimal.

### Testing

Note this template is itself linked to the `skos-vocabulary-editor-staging` instance of the `skos-vocabulary-editor` in Heroku, which is available at `skos-vocabulary-template.openactive.io`. Publishing from the staging instance will therefore create a PR in this repository, which allows it to be easily tested.

When the template is used, only the latest contents are replicated into the new repository. Therefore releases and PRs associated with this repository not be transferred, and can be used for testing.

---

# OpenActive Activity List [![Google Drive](https://img.shields.io/badge/Google%20Drive-4285F4?logo=google-drive&logoColor=white)](https://drive.google.com/drive/folders/11Be4Ang3CRbwdsgsxZAbQLBP37nM1swn?usp=sharing)

This repository holds the data and documentation for the OpenActive list of physical activities.

A Physical Activity is an exercise, sport or other form of bodily movement that involves physical effort. 
Physical activities include not just sports, but also a variety of forms of exercise and fitness classes. 
An Activity List defines a list of physical activities.

A standardised activity list, that provides unique identifiers, labels and descriptions for physical activities can:

* support integration of data published by multiple activity providers
* improve user experience across applications through use of a standard set of activity names and definitions
* enable better discovery and recommendation tools to enable participants to find more opportunities to be active

The list is publicly available at [https://www.openactive.io/activity-list/](https://www.openactive.io/activity-list/).

View [the open data certificate](https://certificates.theodi.org/en/datasets/215260/certificate) for this dataset.

## Dataset Documentation

The dataset is structured according to the [SKOS](https://www.w3.org/TR/skos-primer/) standard for publishing controlled vocabularies.

It consists of:

* a list of terms with an identifier (a URI) and a preferred label (`skos:prefLabel`)
* relationships between terms (`skos:broader`, `skos:narrower` and `skos:related`)
* alternative labels / synonyms (`skos:altLabel`)

### Identifiers

Terms in the list have been assigned a UUID to generate a unique identifier. The URIs for each terms are [Patterned URIs](http://patterns.dataincubator.org/book/patterned-uris.html) that combine these UUIDs with a common prefix:

E.g. Fencing has been assigned a UUID of `92808e60-820c-4ee2-89ec-ea8d99d3f528`. It's URI is `http://openactive.io/activity-list#92808e60-820c-4ee2-89ec-ea8d99d3f528`

### JSON-LD

The [JSON-LD version of the list](https://openactive.io/activity-list/activity-list.jsonld) provides a simple JSON version of the list that conforms to the [JSON-LD](https://www.w3.org/TR/json-ld/) specification.

The JSON-LD version of this controlled vocabulary SHOULD be retrieved frequently using an HTTP GET and cached within an application, to ensure that the most up-to-date version is displayed to the user, while also protecting against network failure when accessing the underlying resource. To access this controlled vocabulary the application MUST GET the URL [`"https://openactive.io/activity-list/activity-list.jsonld"`](https://openactive.io/activity-list/activity-list.jsonld) (note there is no www in the URL) which does not require a specific `Accept` header, and is cached via CDN. The controlled vocabulary is also available via a GET of the URL [`"https://openactive.io/activity-list"`](https://openactive.io/activity-list) using an `Accept` header of `application/ld+json`, for completeness, however this shorter URL MUST NOT be used in production.

## Publication process

The master ('canonical') version of the Activity List is that found at [https://www.openactive.io/activity-list/](https://www.openactive.io/activity-list/). That list is stored within [iQvoc](http://iqvoc.net/), and the list editor can choose to trigger a [workflow](https://github.com/openactive/skos-vocabulary-workflow) to update this repository. The resulting `activity-list.jsonld` is updated and served at `https://openactive.io/activity-list/activity-list.jsonld` via GitHub pages.

Note that new `Concepts` will not be validated unless a machine-readable (no spaces, all lowercase) `notation` is provided with them, and this `notation` value must be unique within the List.

## Licence

The documentation and data in this repository is published under 
the [Creative Commons CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/) license.

