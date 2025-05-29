```
makePSID(userinput_json; codemissings = true)
```

Constructs the PSID panel of individuals using the variables in the input JSON.

Arguments: `userinput_json` - A string naming the input JSON file

Keyword arguments: `codemissings` - A bool indicating whether values detected as missing according to the codebook  will be converted to `missing`. Defaults to true.
