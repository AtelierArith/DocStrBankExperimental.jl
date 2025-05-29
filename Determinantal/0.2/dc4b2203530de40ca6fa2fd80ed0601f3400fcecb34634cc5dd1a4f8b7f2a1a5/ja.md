```
EllEnsemble(L :: AbstractMatrix{T})
```

対称的で非負定義の行列 L から L-アンサンブルを構築します。

```@example
Z = randn(5, 2)
EllEnsemble(Z * Z') #あまり役に立たないと思われる
```

構築時に eigen(L) が呼び出されることに注意してください。これは計算コストが高い場合があります。

L-アンサンブルは、低ランク表現を活用する遅延行列型に基づいても構築できます。上記の例では、LowRank 型を使用することもできます：

```@example
Z = randn(5, 2)
EllEnsemble(LowRank(Z)) # Z*Z' よりも効率的
```
