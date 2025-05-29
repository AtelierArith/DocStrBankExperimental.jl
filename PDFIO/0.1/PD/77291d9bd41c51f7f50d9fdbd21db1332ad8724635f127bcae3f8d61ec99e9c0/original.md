```
    pdDocGetOutline(doc::PDDoc) -> PDOutline
```

Given a PDF document provides the document Outline (Table of Contents) available in the `Document Catalog` dictionary. If document does not have Outline, this method returns `nothing`.

A PDF document may contain a document outline that the conforming reader may display on the screen, allowing the user to navigate interactively from one part of the document to another. The outline consists of a tree-structured hierarchy of outline items (sometimes called bookmarks), which serve as a visual table of contents to display the document’s structure to the user. The user may interactively open and close individual items by clicking them with the mouse. When an item is open, its immediate children in the hierarchy shall become visible on the screen; each child may in turn be open or closed, selectively revealing or hiding further parts of the hierarchy. When an item is closed, all of its descendants in the hierarchy shall be hidden. Clicking the text of any visible item activates the item, causing the conforming reader to jump to a destination or trigger an action associated with the item. - Section 12.3.3 - Document management — Portable document format — Part 1: PDF 1.7

# Example

```
julia> outline = pdDocGetOutline(doc)
555 0 R

julia> iob = IOBuffer();

julia> using AbstractTrees; print_tree(iob, outline)

julia> write(stdout, iob.data)
Contents
├─ Table of Contents
├─ 1. Introduction
├─ 2. Quick Steps - Kernel Compile
│  ├─ 2.1. Precautionary Preparations
│  ├─ 2.2. Minor Upgrading of Kernel
│  ├─ 2.3. For the Impatient
│  ├─ 2.4. Building New Kernel - Explanation of Steps
│  ├─ 2.5. Troubleshooting
...
```
