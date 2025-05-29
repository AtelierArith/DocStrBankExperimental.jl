```julia
toy_mvn_target(dim)

```

テスト用のトイ多変量正規（mvn）ターゲット分布です。すべてのチェーンでi.i.d.サンプリングが可能なように、特化したパス[`ScaledPrecisionNormalPath`](@ref)を使用しています（[`ToyExplorer`](@ref）を介して）。
