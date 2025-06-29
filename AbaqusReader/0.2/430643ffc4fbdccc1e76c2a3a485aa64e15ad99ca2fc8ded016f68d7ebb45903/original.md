```
abaqus_download(model_name; dryrun=false)
```

Download ABAQUS model from Internet. `model_name` is the name of the input file.

Given some model name from documentation, e.g., `et22sfse`, download that file to local file system. This function uses environment variables to determine the download url and place of storage.

In order to use this function, one must set environment variable `ABAQUS_DOWNLOAD_URL`, which determines a location where to download. For example, if the path to model is `https://domain.com/v6.14/books/eif/et22sfse.inp`, `ABAQUS_DOWNLOAD_URL` will be the basename of that path, i.e., `https://domain.com/v6.14/books/eif`.

By default, the model will be downloaded to current directory. If that is not desired, one can set another environment variable `ABAQUS_DOWNLOAD_DIR`, and in that case the file will be downloaded to that directory.

Function call will return full path to downloaded file or nothing, if download is failing because of missing environment variable `ABAQUS_DOWNLOAD_DIR`.
