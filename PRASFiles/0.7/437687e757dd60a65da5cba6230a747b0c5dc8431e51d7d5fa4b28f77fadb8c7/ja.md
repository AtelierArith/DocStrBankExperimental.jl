```
saveshortfall(
    shortfall::AbstractShortfallResult,
    pras_sys::SystemModel,
    outfile::String,
)
```

ShortfallResultまたはShortfallSample ResultをJSON形式で保存します。集約されたシステムおよび地域レベルの結果のみがエクスポートされます。サンプルレベルの結果はエクスポートされません。

# 引数

```
- `shortfall::AbstractShortfallResult`: ShortfallResult (または) ShortfallSamplesResult
- `pras_sys::SystemModel`: PRAS SystemModel
- `outfile::String`: ShortfallResultを保存する場所
```

# 戻り値

  * ShortfallResult (または) ShortfallSamplesResultがJSON形式でエクスポートされる場所。
