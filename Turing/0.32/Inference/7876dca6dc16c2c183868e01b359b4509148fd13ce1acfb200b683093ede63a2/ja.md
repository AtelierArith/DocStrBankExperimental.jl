```
MH(space...)
```

メトロポリス-ヘイスティングスアルゴリズムを構築します。

引数 `space` は次のように指定できます。

  * 空白（つまり `MH()`）、この場合 `MH` は各パラメータの事前分布を提案分布として使用します。
  * `MH` と `Gibbs` を組み合わせてサンプリングするための1つ以上のシンボルのセット、つまり `Gibbs(MH(:m), PG(10, :s))`
  * `Symbol` を `AdvancedMH.Proposal`、`Distribution`、または条件付き提案分布を生成する `Function` にマッピングするペアまたはタプルのイテラブル。
  * 平均ゼロの多変量正規提案に使用する共分散行列。

# 例

デフォルトの `MH` は、`AdvancedMH.StaticProposal` を使用して事前分布からサンプルを提案します。

```julia
@model function gdemo(x, y)
    s² ~ InverseGamma(2,3)
    m ~ Normal(0, sqrt(s²))
    x ~ Normal(m, sqrt(s²))
    y ~ Normal(m, sqrt(s²))
end

chain = sample(gdemo(1.5, 2.0), MH(), 1_000)
mean(chain)
```

また、複数のサンプラーからのサンプリングを組み合わせたい場合は、特定のパラメータをサンプリングするように指定できます。

```julia
@model function gdemo(x, y)
    s² ~ InverseGamma(2,3)
    m ~ Normal(0, sqrt(s²))
    x ~ Normal(m, sqrt(s²))
    y ~ Normal(m, sqrt(s²))
end

# sをMHで、mをPGでサンプリング
chain = sample(gdemo(1.5, 2.0), Gibbs(MH(:s), PG(10, :m)), 1_000)
mean(chain)
```

カスタム分布を使用すると、デフォルトで静的MHが使用されます。

```julia
@model function gdemo(x, y)
    s² ~ InverseGamma(2,3)
    m ~ Normal(0, sqrt(s²))
    x ~ Normal(m, sqrt(s²))
    y ~ Normal(m, sqrt(s²))
end

# sには静的提案を使用し、mには提案の標準偏差が0.25のランダムウォークを使用します。
chain = sample(
    gdemo(1.5, 2.0),
    MH(
        :s => InverseGamma(2, 3),
        :m => Normal(0, 1)
    ),
    1_000
)
mean(chain)
```

`AdvancedMH`インターフェースを使用して明示的な提案を指定します。

```julia
@model function gdemo(x, y)
    s² ~ InverseGamma(2,3)
    m ~ Normal(0, sqrt(s²))
    x ~ Normal(m, sqrt(s²))
    y ~ Normal(m, sqrt(s²))
end

# sには静的提案を使用し、mには提案の標準偏差が0.25のランダムウォークを使用します。
chain = sample(
    gdemo(1.5, 2.0),
    MH(
        :s => AdvancedMH.StaticProposal(InverseGamma(2,3)),
        :m => AdvancedMH.RandomWalkProposal(Normal(0, 0.25))
    ),
    1_000
)
mean(chain)
```

条件付き分布を指定するためにカスタム関数を使用します。

```julia
@model function gdemo(x, y)
    s² ~ InverseGamma(2,3)
    m ~ Normal(0, sqrt(s²))
    x ~ Normal(m, sqrt(s²))
    y ~ Normal(m, sqrt(s²))
end

# sには静的提案を使用し、mには現在のサンプルの周りに中心を持つ条件付き提案を使用します。
chain = sample(
    gdemo(1.5, 2.0),
    MH(
        :s => InverseGamma(2, 3),
        :m => x -> Normal(x, 1)
    ),
    1_000
)
mean(chain)
```

共分散行列を提供すると、`MH`は変換された空間でランダムウォークサンプリングを行い、多変量正規分布から提案を引き出します。提供された行列は、正定値半分であり、正方形でなければなりません。使用法：

```julia
@model function gdemo(x, y)
    s² ~ InverseGamma(2,3)
    m ~ Normal(0, sqrt(s²))
    x ~ Normal(m, sqrt(s²))
    y ~ Normal(m, sqrt(s²))
end

# カスタム分散共分散行列を提供
chain = sample(
    gdemo(1.5, 2.0),
    MH(
        [0.25 0.05;
         0.05 0.50]
    ),
    1_000
)
mean(chain)
```
