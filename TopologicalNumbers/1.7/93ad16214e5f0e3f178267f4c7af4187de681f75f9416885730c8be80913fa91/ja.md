二次チェルン数の二次元相図を指定されたパラメータ範囲で計算します。

```
calcPhaseDiagram(prob::SCProblem, param_range1::T1, param_range2::T2, alg::T3=FHS2(); parallel::T4=UseSingleThread(), plot::Bool=false, progress::Bool=false) where {T1<:AbstractVector,T2<:AbstractVector,T3<:SecondChernAlgorithms,T4<:TopologicalNumbersParallel}
```

# 説明

`calcPhaseDiagram`は、`SCProblem`によって記述された二次元システムの二次チェルン数をパラメータの範囲（`param_range`）にわたって計算し、相図を構築します。`alg`や`parallel`オプションを変更することで、さまざまな計算方法や並列化戦略を柔軟に切り替えることができます。さらに、`plot=true`を設定すると、計算完了後に結果の簡単なプロットが生成されます。

# 引数

  * `prob::SCProblem`:  二次チェルン数計算のための問題設定を含む構造体で、ハミルトニアン、メッシュサイズ、ギャップ情報、その他のパラメータが含まれます。
  * `param_range1::AbstractVector`:  スキャンするパラメータのリストまたは範囲（例：`range(-2.0, 2.0, length=50)`）。各パラメータ値でハミルトニアンが評価され、二次チェルン数が計算されます。
  * `param_range2::AbstractVector`: スキャンするパラメータのリストまたは範囲（例：`range(-2.0, 2.0, length=50)`）。各パラメータ値でハミルトニアンが評価され、二次チェルン数が計算されます。
  * `alg::SecondChernAlgorithms=FHS2()`:  二次チェルン数を計算するために使用されるアルゴリズム。デフォルトは`FHS2()`です。他のアルゴリズムを実装して指定することもできます。
  * `parallel::TopologicalNumbersParallel=UseSingleThread()`:  並列化戦略。デフォルトはシングルスレッド（`UseSingleThread()`）です。分散環境で実行したい場合は、それに応じて指定できます。（現在、二次チェルン数計算はマルチスレッドをサポートしていないことに注意してください。）
  * `plot::Bool=false`:  `true`に設定すると、計算が終了した後に計算結果の簡単なプロットが表示されます。これは、トポロジカル相転移を視覚的に確認するのに役立ちます。
  * `progress::Bool=false`:  `true`に設定すると、ループ計算中に進行状況が表示され、大規模な計算に役立ちます。

# 戻り値

  * `NamedTuple{(:param, :nums)}`: 

      * `param1::AbstractVector`: 入力`param_range1`のコピー。
      * `param2::AbstractVector`: 入力`param_range2`のコピー。
      * `nums::AbstractArray`: 各パラメータに対して計算された二次チェルン数を含む配列。この配列のサイズは（**バンド数** × **param1の数** × **param2の数**）です。
