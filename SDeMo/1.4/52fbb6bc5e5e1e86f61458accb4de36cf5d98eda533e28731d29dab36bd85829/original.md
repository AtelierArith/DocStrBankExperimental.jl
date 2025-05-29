```
features(sdm::SDM)
```

Returns the features stored in the field `X` of the SDM. Note that the features are an array, and this does not return a copy of it – any change made to the output of this function *will* change the content of the SDM features.
