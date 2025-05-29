```
Datasets = load_dataset_file(file_datasets::String)
```

This loads a CSV textfile that lists datasets, which is expected to have the following format:

  * `Name`,`Location`,`Type`, `[Active]`
  * AlpArray,./Seismicity/ALPARRAY/AlpArraySeis.jld2,Point, true
  * Plomerova2022,https://seafile.rlp.net/f/abccb8d3302b4ef5af17/?dl=1,Volume

Note that the first line of the file is skipped.

Here, the meaning of the variables is:

  * `Name`: The name of the dataset to be loaded
  * `Location`: the location of the file (directory and filename) on your local machine, or an url where we can download the file from the web. The url is expected to start with "http".
  * `Type`: type of the dataset (Volume, Surface, Point, Screenshot)
  * `Active`: Do we want this file to be loaded or not? Optional parameter that defaults to `true`
