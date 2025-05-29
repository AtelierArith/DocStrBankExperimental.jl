二次元のベリー位相の位相図を指定されたパラメータ範囲で計算します。

```
calcPhaseDiagram(prob::BPProblem, param_range1::T1, param_range2::T2, alg::T3=BP(); parallel::T4=UseSingleThread(), plot::Bool=false, progress::Bool=false) where {T1<:AbstractVector,T2<:AbstractVector,T3<:BerryPhaseAlgorithms,T4<:TopologicalNumbersParallel}
```

# 説明

`calcPhaseDiagram`は、`BPProblem`によって記述された二次元システムのベリー位相をパラメータの範囲（`param_range`）にわたって計算し、位相図を構築します。`alg`や`parallel`オプションを変更することで、異なる計算方法や並列化戦略を柔軟に切り替えることができます。さらに、`plot=true`を設定すると、計算完了時に結果の簡単なプロットが生成されます。

# 引数

  * `prob::BPProblem`:  ベリー位相計算のための問題設定を含む構造体で、ハミルトニアン、メッシュサイズ、ギャップ情報、その他のパラメータが含まれます。
  * `param_range1::AbstractVector`:  スキャンするパラメータのリストまたは範囲（例：`range(-2.0, 2.0, length=50)`）。ベリー位相を計算するために、各パラメータ値でハミルトニアンが評価されます。
  * `param_range2::AbstractVector`: スキャンするパラメータのリストまたは範囲（例：`range(-2.0, 2.0, length=50)`）。ベリー位相を計算するために、各パラメータ値でハミルトニアンが評価されます。
  * `alg::BerryPhaseAlgorithms=BP()`:  ベリー位相を計算するために使用されるアルゴリズム。デフォルトは`BP()`です。他のアルゴリズムを必要に応じて実装し、指定することができます。
  * `parallel::TopologicalNumbersParallel=UseSingleThread()`:  並列化戦略。デフォルトはシングルスレッド（`UseSingleThread()`）です。分散環境で実行したい場合は、それに応じて指定できます。（現在、ベリー位相計算はマルチスレッドをサポートしていません。）
  * `plot::Bool=false`:  `true`に設定すると、計算が終了した後に計算結果の簡単なプロットが表示されます。これは、トポロジカル位相転移を視覚的に確認するのに役立ちます。
  * `progress::Bool=false`:  `true`に設定すると、ループ計算中に進行状況が表示され、大規模な計算に役立ちます。

# 戻り値

  * `NamedTuple{(:param, :nums)}`: 

      * `param1::AbstractVector`: 入力`param_range1`のコピー。
      * `param2::AbstractVector`: 入力`param_range2`のコピー。
      * `nums::AbstractArray`: 各パラメータに対して計算されたベリー位相を含む配列。この配列のサイズは（**バンド数** × **param1の数** × **param2の数**）です。

# 例

```julia
julia> using TopologicalNumbers
julia> # ハミルトニアンを定義
       H₀(k, p) = KitaevChain(k, p)
julia> # ベリー位相問題を設定
       prob = BPProblem(H₀)
julia> # パラメータ範囲を定義
       param1 = range(-3.0, 3.0, length=4)
       param2 = range(-1.0, 1.0, length=4)
julia> # 位相図を計算（デフォルトのBPアルゴリズム、シングルスレッド、
       # プロットを有効にし、進行状況を表示）
       result = calcPhaseDiagram(prob, param1, param2; plot=true, progress=true)
(param1 = -3.0:2.0:3.0, param2 = -1.0:0.6666666666666666:1.0, nums = [0 1 1 0; 0 1 1 0;;; 0 1 1 0; 0 1 1 0;;; 0 1 1 0; 0 1 1 0;;; 0 1 1 0; 0 1 1 0])

julia> result.param1
-3.0:2.0:3.0

julia> result.param2
-1.0:0.6666666666666666:1.0

julia> result.nums
2×4×4 Array{Int64, 3}:
[:, :, 1] =
 0  1  1  0
 0  1  1  0

[:, :, 2] =
 0  1  1  0
 0  1  1  0

[:, :, 3] =
 0  1  1  0
 0  1  1  0

[:, :, 4] =
 0  1  1  0
 0  1  1  0
```
