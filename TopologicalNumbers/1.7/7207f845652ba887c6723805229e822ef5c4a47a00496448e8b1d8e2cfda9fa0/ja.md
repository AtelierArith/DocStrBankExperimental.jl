指定されたパラメータ範囲に対する第一チェルン数の1次元相図を計算します。

```
calcPhaseDiagram(prob::FCProblem, param_range::T1, alg::T2=FHS(); parallel::T3=UseSingleThread(), plot::Bool=false, progress::Bool=false) where {T1<:AbstractVector,T2<:FirstChernAlgorithms,T3<:TopologicalNumbersParallel}
```

# 説明

`calcPhaseDiagram`は、`FCProblem`によって記述された1次元システムの第一チェルン数を、パラメータの範囲（`param_range`）にわたって計算し、相図を構築します。`alg`や`parallel`オプションを変更することで、異なる計算方法や並列化戦略を柔軟に切り替えることができます。さらに、`plot=true`を設定すると、計算完了後に結果の簡単なプロットが生成されます。

# 引数

  * `prob::FCProblem`:  第一チェルン数計算のための問題設定を含む構造体で、ハミルトニアン、メッシュサイズ、ギャップ情報、その他のパラメータが含まれます。
  * `param_range::AbstractVector`:  スキャンするパラメータのリストまたは範囲（例：`range(-2.0, 2.0, length=50)`）です。ハミルトニアンは、第一チェルン数を計算するために各パラメータ値で評価されます。
  * `alg::FirstChernAlgorithms=FHS()`:  第一チェルン数を計算するために使用されるアルゴリズムです。デフォルトは`FHS()`です。他のアルゴリズムを必要に応じて実装し、指定することができます。
  * `parallel::TopologicalNumbersParallel=UseSingleThread()`:  並列化戦略です。デフォルトはシングルスレッド（`UseSingleThread()`）です。分散環境で実行したい場合は、それに応じて指定できます。（現在、第一チェルン数計算はマルチスレッドをサポートしていないことに注意してください。）
  * `plot::Bool=false`:  `true`に設定すると、計算が終了した後に計算結果の簡単なプロットが表示されます。これは、トポロジカル相転移を視覚的に確認するのに役立ちます。
  * `progress::Bool=false`:  `true`に設定すると、ループ計算中に進行状況が表示され、大規模な計算に役立ちます。

# 戻り値

  * `NamedTuple{(:param, :nums)}`: 

      * `param::AbstractVector`: 入力`param_range`のコピーです。
      * `nums::AbstractMatrix`: 各パラメータに対して計算された第一チェルン数を含む行列です。この行列のサイズは（**バンド数** × **パラメータ値の数**）です。

# 例

```julia
julia> using TopologicalNumbers
julia> # ハミルトニアンを定義
       H₀(k, p) = Haldane(k, p)
       H(k, p) = H₀(k, (1, p, 2.5))
julia> # 第一チェルン数問題を設定
       prob = FCProblem(H)
julia> # パラメータ範囲を定義
       param = range(-π, π, length=10);
julia> # 相図を計算（デフォルトのFHSアルゴリズム、シングルスレッド、
       # プロットを有効にし、進行状況を表示）
       result = calcPhaseDiagram(prob, param; plot=true, progress=true)
(param = -3.141592653589793:0.6981317007977318:3.141592653589793, nums = [0 0; -1 1; -1 1; -1 1; 0 0; 0 0; 1 -1; 1 -1; 1 -1; 0 0])

julia> result.param
-3.141592653589793:0.6981317007977318:3.141592653589793

julia> result.nums
10×2 Matrix{Int64}:
  0   0
 -1   1
 -1   1
 -1   1
  0   0
  0   0
  1  -1
  1  -1
  1  -1
  0   0
```
