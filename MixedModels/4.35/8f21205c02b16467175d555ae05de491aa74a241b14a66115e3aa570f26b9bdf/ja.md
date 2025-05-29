```
savereplicates(f, b::MixedModelFitCollection)
```

[`MixedModelFitCollection`](@ref) に関連付けられたレプリケートを保存します。例えば、[`MixedModelBootstrap`](@ref) を Arrow ファイルとして保存します。

他にも [`restorereplicates`](@ref)、[`saveoptsum`](@ref) があります。

!!! note
    **レプリケートのみ**が保存され、`MixedModelFitCollection` の全内容は保存されません。`restorereplicates` は、フルオブジェクトを復元するためにブートストラップと互換性のあるモデルを必要とします。

