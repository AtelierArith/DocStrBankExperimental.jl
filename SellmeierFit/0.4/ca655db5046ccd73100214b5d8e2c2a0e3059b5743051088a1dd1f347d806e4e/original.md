```
RefractiveIndexInfo(material::String, author::String; kwargs...)
```

Download the CSV file containing the refractive index vs. wavelength data from the RefractiveIndex.Info website, and return the local path to the downloaded file.  By default, the file is named `<first author name>.csv``and stored at`<SellmeierFit package directory>/<material name>/`.

`<first author name>` and `<material name>` correspond to the dataset-distinguishing portion of the URL of the RefractiveIndex.Info webpage.  For example, the webpage for the silicon dioxide dataset published by Malitson et al. is at https://refractiveindex.info/?shelf=main&book=SiO2&page=Malitson, where `SiO2` is `<material name>` and `Malitson` is `<first author name>`.

# Keyword arguments

  * `dir::String=""`: directory name where the downloaded file is stored.
  * `file::String=""`: file name to which the downloaded file is named.
  * `force_download::Bool=false`: true to force download; false to avoid downloading when the file already exists
  * `max_att::Integer=3`: the maximum number of download attempts.
  * `verbose::Bool=true`: true to display messages; false to silence them.
