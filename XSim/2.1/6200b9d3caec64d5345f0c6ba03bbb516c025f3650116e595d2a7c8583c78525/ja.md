# 選択関数

```
select(cohort      ::Cohort,
       n           ::Int64,
       criteria    ::Union{String, Array} = "phenotypes";
       h2          ::Union{Array{Float64}, Float64}=GLOBAL("h2"),
       ve          ::Union{Array{Float64}, Float64}=GLOBAL("Ve"),
       weights     ::Array{Float64, 1}  =[1.0],
       return_log  ::Bool               =false,
       is_random   ::Bool               =false,
       silent      ::Bool               =GLOBAL("silent")

select(cohort::Cohort, ratio::Float64; args...)
```

### 引数

位置引数

  * `cohort` : 個体が選択される`cohort`。
  * `n` : `n`個体が選択される。
  * `ratio` : 個体の`ratio`部分が選択される。
  * `criteria` : 選択に使用される`Criteria`。デフォルトは"phenotypes"で、オプションは["phenotypes", "GBLUP", array]。 "GBLUP"に設定すると、`JWAS`によって遺伝評価が行われ、推定育種値が`criteria`となる。選択のために`criteria`（例：表現型行列）を直接提供することも可能。

キーワード引数

  * `h2` : シミュレーションされた表現型の遺伝率`h2`。
  * `ve` : シミュレーションされた表現型の残差共分散`ve`。
  * `weight` : 選択のための特性の線形係数。選択は、より大きな`weight`を持つ特性に対してより敏感である。負の
  * `return_log` : デフォルトは`false`。選択されたコホートに加えて、選択差と選択応答を返すために`true`に設定。
  * `silent` : デフォルトは`false`。ログメッセージをミュートするために`true`に設定。

### 出力

選択された`cohort`オブジェクトが返される。`return_log`が`true`に設定されている場合、選択されたコホート、選択差、および選択応答を含む`dictionary`オブジェクトが返される。

─────────────────────────────────────────────────────────

### 例

#### 単一特性選択

50のQTLによって制御される単一特性を持つデモゲノムとフェノムを設定します。

```jldoctest
julia> build_demo()
julia> build_phenome(50)
julia> summary()
[ Info: --------- ゲノムサマリー ---------
[ Info: 染色体の数  : 10
[ Info: 
[ Info: 染色体の長さ (cM): 1500.0
[ Info: [150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0]
[ Info: 
[ Info: ロキの数        : 1000
[ Info: [100, 100, 100, 100, 100, 100, 100, 100, 100, 100]
[ Info: 
[ Info: ジェノタイピングエラー      : 0.0
[ Info: 突然変異率         : 0.0
[ Info: 
[ Info: --------- フェノムサマリー ---------
[ Info: 特性の数      : 1
[ Info: 遺伝率 (h2)     : [0.5]
┌ Info: 
│   遺伝的分散 =
│    1×1 Array{Float64,2}:
└     1.0
┌ Info: 
│   残差分散 =
│    1×1 Array{Float64,2}:
└     1.0
[ Info: QTLの数        : [50]
```

100個体のコホートを初期化します。

```jldoctest
julia> cohort = Cohort(100)
```

##### 30個体を選択

```jldoctest
# 上位30個体を選択
julia> cohort_s = select(cohort, 30)
# 同等
julia> cohort_s = select(cohort, 0.3)

[ Info: --------- 選択サマリー ---------
[ Info: 100個体のうち30個体を選択
[ Info: 選択差 (P): [1.174]
[ Info: 選択応答     (G): [0.843]
┌ Info:
│   残差分散 =
│    1×1 Array{Float64,2}:
└     1.0
[ Info: --------- 子孫サマリー ---------
[ Info: コホート (30個体)
[ Info:
[ Info: 育種値の平均:
[ Info: [1.448]
[ Info:
[ Info: 育種値の分散:
[ Info: [0.367]
```

##### 遺伝率`h2`または残差共分散`ve`を割り当て

```jldoctest
# 遺伝率を割り当て
julia> progenies = select(cohort, 30, h2=0.1)

# 遺伝的分散`vg`が1.0の場合の同等
julia> progenies = select(cohort, 30, ve=9.0)

[ Info: --------- 選択サマリー ---------
[ Info: 100個体のうち30個体を選択
[ Info: 選択差 (P): [1.182]
[ Info: 選択応答     (G): [0.338]
┌ Info:
│   残差分散 =
│    1×1 Array{Float64,2}:
└     9.0
[ Info: --------- 子孫サマリー ---------
[ Info: コホート (30個体)
[ Info: 
[ Info: 育種値の平均: 
[ Info: [0.956]
[ Info: 
[ Info: 育種値の分散: 
[ Info: [0.643]
```

##### 負の選択

`is_positive=false`を設定して、個体を昇順にランク付けします。

```jldoctest
julia> progenies = select(cohort, 30, is_positive=false)
[ Info: --------- 選択サマリー ---------
[ Info: 100個体のうち30個体を選択
[ Info: 選択差 (P): [-1.19]
[ Info: 選択応答     (G): [-0.89]
┌ Info: 
│   残差分散 =
│    1×1 Array{Float64,2}:
└     1.0
[ Info: --------- 子孫サマリー ---------
[ Info: コホート (30個体)
[ Info: 
[ Info: 育種値の平均: 
[ Info: [-0.24]
[ Info: 
[ Info: 育種値の分散: 
[ Info: [0.566]
```

##### ランダム選択

```jldoctest
julia> progenies = select(cohort, 30, is_random=true)
[ Info: --------- 選択サマリー ---------
[ Info: 100個体のうち30個体を選択
[ Info: 選択差 (P): [-0.06]
[ Info: 選択応答     (G): [-0.191]
┌ Info: 
│   残差分散 =
│    1×1 Array{Float64,2}:
└     1.0
[ Info: --------- 子孫サマリー ---------
[ Info: コホート (30個体)
[ Info: 
[ Info: 育種値の平均: 
[ Info: [0.441]
[ Info: 
[ Info: 育種値の分散: 
[ Info: [0.946]
```

##### 複数パラメータによる選択

上記の複数のパラメータを1つの選択で指定することが可能です。ユーザーは、パラメータをキーワード引数として囲むか、`dictionary`オブジェクトを通じて渡すことができます。

```jldoctest
# キーワード引数
julia> progenies = select(cohort, 30, h2=0.3, is_positive=false)

# 同等
julia> args = Dict(:h2=>0.3,
                   :is_positive=>false)
julia> progenies = select(cohort, 30; args...)

[ Info: --------- 選択サマリー ---------
[ Info: 100個体のうち30個体を選択
[ Info: 選択差 (P): [-1.086]
[ Info: 選択応答     (G): [-0.486]
┌ Info: 
│   残差分散 =
│    1×1 Array{Float64,2}:
└     2.3333333333333335
[ Info: --------- 子孫サマリー ---------
[ Info: コホート (30個体)
[ Info: 
[ Info: 育種値の平均: 
[ Info: [0.154]
[ Info: 
[ Info: 育種値の分散: 
[ Info: [0.818]
```

─────────────────────────────────────────────────────────

#### 複数特性選択

50のQTLによって制御される単一特性を持つデモゲノムとフェノムを設定します。

```jldoctest
julia> build_demo()
julia> summary()
[ Info: --------- ゲノムサマリー ---------
[ Info: 染色体の数  : 10
[ Info: 
[ Info: 染色体の長さ (cM): 1500.0
[ Info: [150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0]
[ Info: 
[ Info: ロキの数        : 1000
[ Info: [100, 100, 100, 100, 100, 100, 100, 100, 100, 100]
[ Info: 
[ Info: ジェノタイピングエラー      : 0.0
[ Info: 突然変異率         : 0.0
[ Info: 
[ Info: --------- フェノムサマリー ---------
[ Info: 特性の数      : 2
[ Info: 遺伝率 (h2)     : [0.5, 0.5]
┌ Info: 
│   遺伝的分散 =
│    2×2 Array{Float64,2}:
│     1.0  0.0
└     0.0  1.0
┌ Info: 
│   残差分散 =
│    2×2 Array{Float64,2}:
│     1.0  0.0
└     0.0  1.0
[ Info: QTLの数        : [3 8]
```

100個体のコホートを初期化します。

```jldoctest
julia> cohort = Cohort(100)
```

##### 複数特性の遺伝率を割り当て

```jldoctest
julia> progenies = select(cohort, 30, h2=[0.9, 0.3])
[ Info: --------- 選択サマリー ---------
[ Info: 100個体のうち30個体を選択
[ Info: 選択差 (P): [0.468 1.028]
[ Info: 選択応答     (G): [0.383 0.636]
┌ Info: 
│   残差分散 =
│    2×2 Array{Float64,2}:
│     0.111111  0.0
└     0.0       2.33333
[ Info: --------- 子孫サマリー ---------
[ Info: コホート (30個体)
[ Info: 
[ Info: 育種値の平均: 
[ Info: [-0.889 0.28]
[ Info: 
[ Info: 育種値の分散: 
[ Info: [0.947 0.625]
```

##### 残差共分散を介して特性の相関を割り当て

```jldoctest
julia> progenies = select(cohort, 30, ve=[1   0.3
                                          0.3   1])
[ Info: --------- 選択サマリー ---------
[ Info: 100個体のうち30個体を選択
[ Info: 選択差 (P): [0.866 0.925]
[ Info: 選択応答     (G): [0.662 0.762]
┌ Info: 
│   残差分散 =
│    2×2 Array{Float64,2}:
│     1.0  0.3
└     0.3  1.0
[ Info: --------- 子孫サマリー ---------
[ Info: コホート (30個体)
[ Info: 
[ Info: 育種値の平均: 
[ Info: [-0.608 0.406]
[ Info: 
[ Info: 育種値の分散: 
[ Info: [0.549 0.476]
```

##### 複数特性の選択指数を導出

`weights`パラメータにベクトルを割り当てて、重みと表現型の線形結合である選択指数を導出します。この例では、遺伝率がそれぞれ0.3と0.8の2つの特性を示します。そして、より遺伝率の高い2番目の特性に重みを置き、1番目の特性を負に選択することができます。

```jldoctest
julia> progenies = select(cohort, 30, h2=[.3, .8], weights=[-0.1, 0.9])
[ Info: --------- 選択サマリー ---------
[ Info: 100個体のうち30個体を選択
[ Info: 選択差 (P): [-0.318 1.027]
[ Info: 選択応答     (G): [-0.233 0.869]
┌ Info:
│   残差分散 =
│    2×2 Array{Float64,2}:
│     2.33333  0.0
└     0.0      0.25
[ Info: --------- 子孫サマリー ---------
[ Info: コホート (30個体)
[ Info:
[ Info: 育種値の平均:
[ Info: [-1.508 0.513]
[ Info:
[ Info: 育種値の分散:
[ Info: [1.053 0.458]
```
