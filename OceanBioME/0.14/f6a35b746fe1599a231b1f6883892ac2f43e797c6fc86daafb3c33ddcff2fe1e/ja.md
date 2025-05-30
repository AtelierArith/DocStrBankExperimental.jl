```
ScaleNegativeTracers(; tracers, scalefactors = ones(length(tracers)), warn = false, invalid_fill_value = NaN)
```

`tracers`をスケールして負の値が出ないようにする修飾子を構築します。使用例：

```julia
modifier = ScaleNegativeTracers((:P, :Z, :N))
biogeochemistry = Biogeochemistry(...; modifier)
```

このメソッドは、[`ZeroNegativeTracers`](@ref)と比較して負のトレーサー値を引き起こす数値エラーを防ぐためのより良いがまだ不完全な方法です。詳細は[githubの議論](https://github.com/OceanBioME/OceanBioME.jl/discussions/48)を参照してください。

将来的な計画には、理想的な代替手段として、正の値を保持するタイムステッピングスキームの実装が含まれています。

~~`warn`がtrueの場合、スケーリングは警告を発生させます。~~

`invalid_fill_value`は、合計が0未満の場合にセルの総内容を設定する値を指定します（これは、トレーサーの総保存が強制できないことを意味します）。この値が`NaN`以外に設定されると、このスキームはもはや質量を保存しません。これは、クラッシュを引き起こすスプリアスな数値を防ぐために役立つかもしれませんが、質量があまりにも逸脱しないように注意が必要です。

このスキームは、[NEMO-PISCES](https://www.nemo-ocean.eu/)で使用されているものに似ていますが、彼らは値ではなく傾向をスケーリングします。一方、他の地球システムモデルは、負のトレーサーをゼロに設定するだけです。例えば、[NCARのMARBL](https://marbl-ecosys.github.io/versions/latest_release/index.html)や[NEMO-TOPAZ2](https://zenodo.org/records/2648099)は、質量を保存しません。より複雑なスキームも存在し、例えば[ROMS-BECS](https://zenodo.org/records/3988618)は、各コンポーネントが順番に更新される暗黙的反復アプローチを使用して質量保存を保証しますが、数値精度が犠牲になる可能性があります。
