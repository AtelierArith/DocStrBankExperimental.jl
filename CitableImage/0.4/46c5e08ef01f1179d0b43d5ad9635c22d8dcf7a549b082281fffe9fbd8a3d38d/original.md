Compose markdown wrapping IIIF URL for image linked to an image citation tool installation.

```julia
linkedMarkdownImage(ict, img, service; ht, caption)

```

# Arguments

  * `ict` URL of an instance of the CiteArchitecture ImageCitationTool.
  * `img` `Cite2Urn` for an image.
  * `service` `IIIFService`
  * `ht` Height of resulting image in pixels.
  * `caption` Caption to embed in resulting linked markdown string.
