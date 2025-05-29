```
Potrace(mask; [ϵ])
Potrace(mask, var₁ => agg₁, ..., varₙ => aggₙ; [ϵ])
```

SelingerのPotraceアルゴリズムを使用して2D画像データ上のポリゴンをトレースします。

列`mask`に格納されたカテゴリはバイナリマスクに変換され、その後マルチポリゴンにトレースされます。オプション`ϵ`が提供されると、Selingerの簡略化アルゴリズムに渡されます。

変数`varᵢ`の重複は集約関数`aggᵢ`で集約されます。変数`varᵢ`に対して集約関数が定義されていない場合、デフォルトの集約関数が使用されます。デフォルトの集約関数は連続変数の場合は`mean`、それ以外の場合は`first`です。

# 例

```julia
Potrace(:mask, ϵ=0.1)
Potrace(1, 1 => last, 2 => maximum)
Potrace(:mask, :a => first, :b => minimum)
Potrace("mask", "a" => last, "b" => maximum)
```

## 参考文献

  * Selinger, P. 2003. [Potrace: A polygon-based tracing algorithm](https://potrace.sourceforge.net/potrace.pdf)
