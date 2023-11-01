# Quick BOI: Source

Source text and code for Quick BOI, a reference handbook for the Beginning of Infinity.

Published at: https://ceramic-sf.github.io/2023/10/24/quick-boi.html


## Mechanics

The book is markdown and contains hyperlinks to prior headings.

A python script finds hyperlinks and creates graphs showing links/hierarchies.
It generates plant UML diagrams for those links (`./diagrams/complete/`).
It also inserts links in each section to the relevant diagram.

A plant UML processor converts .uml to .svg. A markdown processor

## How to generate book

1. Text in `bolq.md` is the definitive source for content.
2. Delete all `.puml` files in `./diagrams/complete`.
3. Delete all `.svg` files in `.out/diagrams/complete`.
4. Run `scripts/make_book_with_diagrams.py`. This creates diagrams (`.puml` format, using `scripts/diagram_generator.py`, saved in `./diagrams/complete`) and generates a new `bolq_with_diagrams.md`.
5. Using VS Code, `CTRL`+`SHIFT`+`P` to find and run `PlantUML export workspace diagrams`, selecting `svg` format. New diagrams are made in  `./out/diagrams/complete`. This will take some time.
6. To preview convert to HTML or PDF using a markdown generator. E.g., Using VS Code, `CTRL`+`SHIFT`+`P` to find and run `Markdown PDF: Export (html)`.
7. Open `bolq_with_diagrams.html` using a web browser to see the content.
8. Do not edit content `bolq_with_diagrams.md` as it is not the definitive source and will be overwritten. Change `bolq.md` and re-run `./scripts/make_book_with_diagrams.py` instead.

## Publish the book

The content is published as a blog post generated with github pages from content here:

https://github.com/ceramic-sf/ceramic-sf.github.io/blob/main/docs/_posts/2023-10-24-quick-boi.md

### Text
To update that post, copy everything in teh generated `bolq_with_diagrams.md` and place below the blog post header.

```
---
layout: post
title:  "Quick BOI: A Reference Handbook for The Beginning of Infinity"
categories:
---

[here]
```
### Diagram links

The generated book (`bolq_with_diagrams.md`) has diagrams with image links of the form:

`![connections_for_incremental_truth](./out/diagrams/complete/bolq_diagram_incremental_truth/bolq_diagram_incremental_truth.svg)`

The blog-based book links must have the following format:

`![connections_for_incremental_truth](/assets/images_quick_boi/bolq_diagram_incremental_truth/bolq_diagram_incremental_truth.svg)`

Select all `./out/diagrams/complete` and update to `/assets/images_quick_boi/`.

### Diagram images

Copy the images to the blog repository:
- From: `./out/diagrams/complete/` (in this repo)
- To: `docs/assets/images_quick_boi/` (in blog repo github.com/ceramic-sf/ceramic-sf.github.io)

### Test the published book

In the blog repo (https://github.com/ceramic-sf/ceramic-sf.github.io):
```
cd docs
bundle exec jekyll serve
```
Navigate to http://127.0.0.1:4000/