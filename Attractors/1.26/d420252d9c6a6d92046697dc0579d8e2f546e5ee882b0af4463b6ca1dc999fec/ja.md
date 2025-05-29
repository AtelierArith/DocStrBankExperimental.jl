```
basins_fractions(
    mapper::AttractorMapper,
    ics::Union{AbstractVector, Function};
    kwargs...
)
```

動的システムの吸引域の状態空間の割合 `fs` を、初期条件を吸引子にマッピングすることで近似します。`mapper` は [`DynamicalSystem`](@ref) への参照を含んでいます。割合は、各吸引子に到達した初期条件の数の比率です。

使用する初期条件は `ics` によって定義されます。これは次のいずれかです：

  * 初期条件の `AbstractVector` で、すべてが使用されます。通常、これは `StateSpaceSet` です。
  * ランダムな初期条件を生成する0引数関数 `ics()` です。この場合、N個のランダムな初期条件が選ばれます。こうした関数を生成するには [`statespace_sampler`](@ref) を参照してください。

## 戻り値

この関数は常に `fractions` を返します。これは辞書で、キーは各吸引子に与えられたラベル（常に異なる吸引子を列挙する整数）であり、値はそれぞれの吸引域の割合です。ラベル `-1` は、`mapper` が吸引子にマッチできなかった初期条件に与えられます（これは `mapper` のタイプに依存します）。

`ics` が `StateSpaceSet` の場合、関数は `labels` も返します。これは `ics` と同じ長さの *ベクトル* で、各初期条件がマッピングされたラベルを含みます。

すべての可能な `mapper` タイプについては [`AttractorMapper`](@ref) を参照し、`basins_fractions` を呼び出した後に [`extract_attractors`](@ref) を使用して `mapper` から保存された吸引子を抽出してください。また、[`convergence_and_basins_fractions`](@ref) も参照してください。

## キーワード引数

  * `N = 1000`: `ics` が関数の場合に生成するランダムな初期条件の数。
  * `show_progress = true`: プロセスの進行状況バーを表示します。
