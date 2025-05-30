```
ScaleNegativeTracers(; tracers, scalefactors = ones(length(tracers)), warn = false, invalid_fill_value = NaN)
```

`tracers`をスケーリングして負の値がないようにする修飾子を構築します。使用例：

```julia
modifier = ScaleNegativeTracers((:P, :Z, :N))
biogeochemistry = Biogeochemistry(...; modifier)
```

このメソッドは、[`ZeroNegativeTracers`](@ref)と比較して負のトレーサー値につながる数値エラーを防ぐためのより良いがまだ不完全な方法です。詳細は[githubの議論](https://github.com/OceanBioME/OceanBioME.jl/discussions/48)を参照してください。

将来の計画には、理想的な代替手段として、正の値を保持するタイムステッピングスキームの実装が含まれています。

~~`warn`がtrueの場合、スケーリングは警告を発生させます。~~

`invalid_fill_value`は、合計が0未満の場合にセルの総内容を設定する値を指定します（これは、トレーサーの総保存が強制できないことを意味します）。値が`NaN`以外に設定されている場合、このスキームはもはや質量を保存しません。これは、クラッシュを引き起こすスプリアスな数値を防ぐために役立つかもしれませんが、質量があまりにも逸脱しないように注意が必要です。

このスキームは、[NEMO-PISCES](https://www.nemo-ocean.eu/)で使用されているものに似ていますが、彼らは値ではなく傾向をスケーリングします。一方、他の地球システムモデルは、負のトレーサーをゼロに設定するだけです。例えば、[NCARのMARBL](https://marbl-ecosys.github.io/versions/latest_release/index.html)や[NEMO-TOPAZ2](https://zenodo.org/records/2648099)は、質量を保存しません。より複雑なスキームも存在し、例えば[ROMS-BECS](https://zenodo.org/records/3988618)は、各コンポーネントが順次更新されて質量保存を保証する暗黙的反復アプローチを使用しますが、数値精度の犠牲を伴う可能性があります。
