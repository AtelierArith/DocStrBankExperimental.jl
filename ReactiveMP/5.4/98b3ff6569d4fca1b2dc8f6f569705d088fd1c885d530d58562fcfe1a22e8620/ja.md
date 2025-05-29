```
@node(fformtype, sdtype, interfaces_list)
```

`@node` マクロは `fformtype` 型オブジェクトのためのノードを作成します。事前定義されたノードのリストを取得するには `?is_predefined_node` を使用してください。

# 引数

  * `fformtype`: 既存の型識別子、例えば `Normal` または関数型識別子、例えば `typeof(+)`
  * `sdtype`: `Stochastic` または `Deterministic` のいずれか。関数的関係のタイプを定義します
  * `interfaces_list`: ファクターノードの固定エッジリストを定義します。慣例として最初の要素は `out` であるべきです。例: `[ out, mean, variance ]`

注意: `interfaces_list` には `_` シンボルを含む名前を含めてはいけません。これはノードオブジェクトの周りの結合事後分布を識別するために予約されています。

# 例

```julia

struct MyNormalDistribution
    mean :: Float64
    var  :: Float64
end

@node MyNormalDistribution Stochastic [ out, mean, var ]
```

```julia

@node typeof(+) Deterministic [ out, in1, in2 ]
```

# 利用可能なノードのリスト

`?is_predefined_node` を参照してください。
