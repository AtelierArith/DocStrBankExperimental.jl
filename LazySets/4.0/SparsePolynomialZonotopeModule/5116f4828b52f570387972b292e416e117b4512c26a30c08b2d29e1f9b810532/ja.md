```
rand(::Type{SparsePolynomialZonotope}; [N]::Type{<:Real}=Float64,
     [dim]::Int=2, [nparams]::Int=2, [maxdeg]::Int=3,
     [num_dependent_generators]::Int=-1,
     [num_independent_generators]::Int=-1, [rng]::AbstractRNG=GLOBAL_RNG,
     [seed]::Union{Int, Nothing}=nothing)
```

ランダムなスパース多項式ゾノトープを作成します。

### 入力

  * `SparsePolynomialZonotope`   – ディスパッチ用の型
  * `N`                          – (オプション、デフォルト: `Float64`) 数値型
  * `dim`                        – (オプション、デフォルト: 2) 次元
  * `nparams`                    – (オプション、デフォルト: 2) パラメータの数
  * `maxdeg`                     – (オプション、デフォルト: 3) 各パラメータの最大次数
  * `num_dependent_generators`   – (オプション、デフォルト: `-1`) 従属生成子の数（下記のコメントを参照）
  * `num_independent_generators` – (オプション、デフォルト: `-1`) 独立生成子の数（下記のコメントを参照）
  * `rng`                        – (オプション、デフォルト: `GLOBAL_RNG`) ランダム数生成器
  * `seed`                       – (オプション、デフォルト: `nothing`) 再シード用のシード

### 出力

ランダムなスパース多項式ゾノトープ。

### アルゴリズム

すべての数値は平均0、標準偏差1の正規分布に従います。

生成子の数は、引数`num_dependent_generators`と`num_independent_generators`で制御できます。負の値の場合、範囲`dim:2*dim`内のランダムな数を選択します（ただし、`dim == 1`の場合は単一の生成子のみを作成します）。冗長な単項式が生成されると、最終的な生成子の数は少なくなる可能性があることに注意してください。
