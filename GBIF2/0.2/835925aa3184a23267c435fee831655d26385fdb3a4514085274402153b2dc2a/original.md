```
occurrence_download([key::String]; [filename])
```

Download the data for an occurrence key returned by `occurrence_request`, or without arguments download the last result of `occurrence_request`.

Note that `occurrence_download` depends on gbif.org preparing the download. Prior to it will give a 404 error as the page will not be found.

The `filename` keyword can be used to name the resulting file.

# Example

Request all the common mynor birds below 100m of elevation:

```
sp = species_match("Acridotheres tristis");
token = occurrence_request(sp, username="my_gbif_username", elevation=<(100))
write("mydownloadtoken", string(token)) # save it just in case
# wait for your download to be prepared
# If you need to, read the token again:
token = readlines("mydownloadtoken")[1]
# And download it
filename = GBIF2.occurrence_download(token)
```
