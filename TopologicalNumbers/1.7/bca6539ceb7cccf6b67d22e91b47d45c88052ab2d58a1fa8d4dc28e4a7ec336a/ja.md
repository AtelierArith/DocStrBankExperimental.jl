指定されたパラメータ範囲に対する第二チェルン数の1次元相図を計算します。

```
calcPhaseDiagram(prob::SCProblem, param_range::T1, alg::T2=FHS2(); parallel::T3=UseSingleThread(), plot::Bool=false, progress::Bool=false) where {T1<:AbstractVector,T2<:SecondChernAlgorithms,T3<:TopologicalNumbersParallel}
```

# 説明

`calcPhaseDiagram`は、`SCProblem`によって記述された1次元系の第二チェルン数を、パラメータの範囲（`param_range`）にわたって計算し、相図を構築します。`alg`や`parallel`オプションを変更することで、異なる計算方法や並列化戦略を柔軟に切り替えることができます。さらに、`plot=true`を設定すると、計算完了後に結果の簡単なプロットが生成されます。

# 引数

  * `prob::SCProblem`:  第二チェルン数計算のための問題設定を含む構造体で、ハミルトニアン、メッシュサイズ、充填バンド数、ギャップ情報、その他のパラメータが含まれます。デフォルトは半充填バンドの場合です。
  * `param_range::AbstractVector`:  スキャンするパラメータのリストまたは範囲（例：`range(-2.0, 2.0, length=50)`）です。第二チェルン数を計算するために、各パラメータ値でハミルトニアンが評価されます。
  * `alg::SecondChernAlgorithms=FHS2()`:  第二チェルン数を計算するために使用されるアルゴリズムです。デフォルトは`FHS2()`です。必要に応じて他のアルゴリズムを実装して指定できます。
  * `parallel::TopologicalNumbersParallel=UseSingleThread()`:  並列化戦略です。デフォルトはシングルスレッド（`UseSingleThread()`）です。分散環境で実行したい場合は、それに応じて指定できます。
  * `plot::Bool=false`:  `true`に設定すると、計算が終了した後に計算結果の簡単なプロットが表示されます。これは、トポロジカル相転移を視覚的に確認するのに役立ちます。
  * `progress::Bool=false`:  `true`に設定すると、ループ計算中に進行状況が表示され、大規模な計算に役立ちます。

# 戻り値

  * `NamedTuple{(:param, :nums)}`: 

      * `param::AbstractVector`: 入力`param_range`のコピーです。
      * `nums::AbstractVector`: 各パラメータに対して計算された第二チェルン数を含むベクトルです。

# 例

```julia
julia> using TopologicalNumbers
julia> # ハミルトニアンを定義
       H₀(k, p) = LatticeDirac(k, p)
julia> N = 10; # 各方向のk点の数
julia> # 第二チェルン数問題を設定
       prob = SCProblem(H₀, N)
julia> # パラメータ範囲を定義
       param = range(-4.9, 4.9, length=4)
julia> # 相図を計算（デフォルトのFHS2アルゴリズムを使用し、シングルスレッドで、
       # プロットを有効にし、進行状況を表示）
       result = calcPhaseDiagram(prob, param; plot=true, progress=true)
(param = -4.9:3.2666666666666666:4.9, nums = [0.0010237313095167136, -2.0667333080974726, 2.1572606447321445, -0.0009805850180973081])

julia> result.param
-4.9:3.2666666666666666:4.9

julia> result.nums
4-element Vector{Float64}:
  0.0010237313095167136
 -2.0667333080974726
  2.1572606447321445
 -0.0009805850180973081
```
