指定されたパラメータ範囲に対する$\mathbb{Z}_2$数の1次元相図を計算します。

```
calcPhaseDiagram(prob::Z2Problem, param_range::T1, alg::T2=Shio(); parallel::T3=UseSingleThread(), plot::Bool=false, progress::Bool=false) where {T1<:AbstractVector,T2<:Z2Algorithms,T3<:TopologicalNumbersParallel}
```

# 説明

`calcPhaseDiagram`は、`Z2Problem`によって記述された1次元システムの$\mathbb{Z}_2$数を、パラメータの範囲（`param_range`）にわたって計算し、相図を構築します。`alg`や`parallel`オプションを変更することで、異なる計算方法や並列化戦略を柔軟に切り替えることができます。さらに、`plot=true`を設定すると、計算完了後に結果の簡単なプロットが生成されます。

# 引数

  * `prob::Z2Problem`:  $\mathbb{Z}_2$数計算のための問題設定を含む構造体で、ハミルトニアン、メッシュサイズ、ギャップ情報、その他のパラメータが含まれます。
  * `param_range::AbstractVector`:  スキャンするパラメータのリストまたは範囲（例：`range(-2.0, 2.0, length=50)`）です。ハミルトニアンは、$\mathbb{Z}_2$数を計算するために各パラメータ値で評価されます。
  * `alg::Z2Algorithms=Shio()`:  $\mathbb{Z}_2$数を計算するために使用されるアルゴリズム。デフォルトは`Shio()`です。他のアルゴリズムを必要に応じて実装し、指定することができます。
  * `parallel::TopologicalNumbersParallel=UseSingleThread()`:  並列化戦略。デフォルトはシングルスレッド（`UseSingleThread()`）です。分散環境で実行したい場合は、それに応じて指定できます。（現在、$\mathbb{Z}_2$数計算はマルチスレッドをサポートしていないことに注意してください。）
  * `plot::Bool=false`:  `true`に設定すると、計算が終了した後に計算結果の簡単なプロットが表示されます。これは、トポロジカル相転移を視覚的に確認するのに役立ちます。
  * `progress::Bool=false`:  `true`に設定すると、ループ計算中に進行状況が表示され、大規模な計算に役立ちます。

# 戻り値

  * `NamedTuple{(:param, :nums)}`: 

      * `param::AbstractVector`: 入力`param_range`のコピー。
      * `nums::AbstractMatrix`: 各パラメータに対して計算された$\mathbb{Z}_2$数を含む行列。この行列のサイズは（**バンド数** × **パラメータ値の数**）です。

# 例

```julia
julia> using TopologicalNumbers
julia> # ハミルトニアンを定義
       H₀(k, p) = BHZ(k, p)
       H(k, p) = H₀(k, (p, 0.25))
julia> # $\mathbb{Z}_2$数問題を設定
       prob = Z2Problem(H)
julia> # パラメータ範囲を定義
       param = range(-2, 2, length=10)
julia> # 相図を計算（デフォルトのShioアルゴリズム、シングルスレッド、
       # プロットを有効にし、進行状況を表示）
       result = calcPhaseDiagram(prob, param; plot=true, progress=true)
(param = -2.0:0.4444444444444444:2.0, nums = [0 0; 0 0; 0 0; 1 1; 1 1; 1 1; 1 1; 0 0; 0 0; 0 0])

julia> result.param
-2.0:0.4444444444444444:2.0

julia> result.nums
10×2 Matrix{Int64}:
 0  0
 0  0
 0  0
 1  1
 1  1
 1  1
 1  1
 0  0
 0  0
 0  0
```
