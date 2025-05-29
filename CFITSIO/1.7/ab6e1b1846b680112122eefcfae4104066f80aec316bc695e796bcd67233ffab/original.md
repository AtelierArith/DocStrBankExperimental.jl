```
fits_hdr2str(f::FITSFile, nocomments::Bool=false)
```

Return the header of the CHDU as a string. If `nocomments` is `true`, comment cards are stripped from the output.
