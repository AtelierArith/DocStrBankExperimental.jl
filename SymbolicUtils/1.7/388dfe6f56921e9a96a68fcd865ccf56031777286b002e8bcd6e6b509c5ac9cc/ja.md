```
simplify_fractions(x; polyform=false)
```

`Div`ノードを見つけ、分子と分母の因子のセットをキャンセルすることで簡略化します。`polyform=true`の場合、多項式GCDを見つける目的でPolyFormに変換された因子はそのまま残されます。PolyFormsはSymbolicUtils式とは異なる`hash`を持つため、`polyform=true`の場合、`substitute`が機能しない可能性があることに注意してください。
