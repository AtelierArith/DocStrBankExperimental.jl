```
saveshortfall(
    shortfall::AbstractShortfallResult,
    pras_sys::SystemModel,
    outfile::String,
)
```

Save ShortfallResult or ShortfallSample Result in JSON format. Only aggregate system and region level results are exported. Sample level results are not exported..

# Arguments

```
- `shortfall::AbstractShortfallResult`: ShortfallResult (or) ShortfallSamplesResult
- `pras_sys::SystemModel`: PRAS SystemModel
- `outfile::String`: Location to save the ShortfallResult
```

# Returns

  * Location where ShortfallResult (or) ShortfallSamplesResult is exported in JSON format.
