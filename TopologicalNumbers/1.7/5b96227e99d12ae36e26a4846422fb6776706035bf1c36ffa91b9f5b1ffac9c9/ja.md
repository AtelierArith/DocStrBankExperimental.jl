$$
\mathbb{Z}_2
$$

数の二次元相図を指定されたパラメータ範囲で計算します。

```
calcPhaseDiagram(prob::Z2Problem, param_range1::T1, param_range2::T2, alg::T3=Shio(); parallel::T4=UseSingleThread(), plot::Bool=false, progress::Bool=false) where {T1<:AbstractVector,T2<:AbstractVector,T3<:Z2Algorithms,T4<:TopologicalNumbersParallel}
```

# 説明

`calcPhaseDiagram`は、`Z2Problem`によって記述された二次元システムの$\mathbb{Z}_2$数を、パラメータの範囲（`param_range`）にわたって計算し、相図を構築します。`alg`や`parallel`オプションを変更することで、異なる計算方法や並列化戦略を柔軟に切り替えることができます。さらに、`plot=true`を設定すると、計算完了後に結果の簡単なプロットが生成されます。

# 引数

  * `prob::Z2Problem`:  $\mathbb{Z}_2$数計算のための問題設定を含む構造体で、ハミルトニアン、メッシュサイズ、ギャップ情報、その他のパラメータが含まれます。
  * `param_range1::AbstractVector`:  スキャンするパラメータのリストまたは範囲（例：`range(-2.0, 2.0, length=50)`）。ハミルトニアンは、$\mathbb{Z}_2$数を計算するために各パラメータ値で評価されます。
  * `param_range2::AbstractVector`: スキャンするパラメータのリストまたは範囲（例：`range(-2.0, 2.0, length=50)`）。ハミルトニアンは、$\mathbb{Z}_2$数を計算するために各パラメータ値で評価されます。
  * `alg::Z2Algorithms=Shio()`:  $\mathbb{Z}_2$数を計算するために使用されるアルゴリズム。デフォルトは`Shio()`です。他のアルゴリズムを実装して指定することもできます。
  * `parallel::TopologicalNumbersParallel=UseSingleThread()`:  並列化戦略。デフォルトはシングルスレッド（`UseSingleThread()`）です。分散環境で実行したい場合は、それに応じて指定できます。（現在、$\mathbb{Z}_2$数計算はマルチスレッドをサポートしていないことに注意してください。）
  * `plot::Bool=false`:  `true`に設定すると、計算が終了した後に計算結果の簡単なプロットが表示されます。これは、トポロジカル相転移を視覚的に確認するのに役立ちます。
  * `progress::Bool=false`:  `true`に設定すると、ループ計算中に進行状況が表示され、大規模な計算に役立ちます。

# 戻り値

  * `NamedTuple{(:param, :nums)}`: 

      * `param1::AbstractVector`: 入力`param_range1`のコピー。
      * `param2::AbstractVector`: 入力`param_range2`のコピー。
      * `nums::AbstractArray`: 各パラメータに対して計算された$\mathbb{Z}_2$数を含む配列。この配列のサイズは（**バンド数** × **param1の数** × **param2の数**）です。

# 例

```julia
julia> using TopologicalNumbers
julia> # ハミルトニアンを定義
       H₀(k, p) = BHZ(k, p)
julia> # $\mathbb{Z}_2$数問題を設定
       prob = Z2Problem(H₀)
julia> # パラメータ範囲を定義
       param1 = range(-2, 2, length=4);
       param2 = range(-0.4, 0.4, length=4)
julia> # 相図を計算（デフォルトのShioアルゴリズム、シングルスレッド、
       # プロットを有効にし、進行状況を表示）
       result = calcPhaseDiagram(prob, param1, param2; plot=true, progress=true)
(param1 = -2.0:1.3333333333333333:2.0, param2 = -0.4:0.26666666666666666:0.4, nums = [0 1 1 0; 0 1 1 0;;; 0 0 0 0; 0 0 0 0;;; 0 0 0 0; 0 0 0 0;;; 0 1 1 0; 0 1 1 0])

julia> result.param1
-2.0:1.3333333333333333:2.0

julia> result.param2
-0.4:0.26666666666666666:0.4

julia> result.nums
2×4×4 Array{Int64, 3}:
[:, :, 1] =
 0  1  1  0
 0  1  1  0

[:, :, 2] =
 0  0  0  0
 0  0  0  0

[:, :, 3] =
 0  0  0  0
 0  0  0  0

[:, :, 4] =
 0  1  1  0
 0  1  1  0
```
