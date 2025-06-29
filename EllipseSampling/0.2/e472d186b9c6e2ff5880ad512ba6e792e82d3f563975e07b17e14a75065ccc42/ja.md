```
generate_N_clustered_points(num_points::Int, e::Ellipse; start_point_shift::Float64=rand(), sqrt_distortion::Float64=0.0)
```

`num_points` 個の点を、`e` に含まれるパラメータで定義された楕円上に配置します。点は、2 行 `num_points` 列の配列として返され、各点は列に格納されます。

# 引数

  * `num_points`: 楕円上に配置される点の正の整数の数。
  * `e`: 楕円を定義する有効な [`EllipseSampling.Ellipse`](@ref) 構造体。

# キーワード引数

  * `start_point_shift`: 数値 ∈ [0.0,1.0]。デフォルトは `rand()`（[0.0,1.0] で定義）であり、デフォルトではこの関数が呼ばれるたびに異なる点のセットが生成されます。
  * `sqrt_distortion`: 数値 ∈ [0.0,1.0]。デフォルトは `0.0` であり、デフォルトではこの関数はパラメータ `t` に関して楕円 `e` 上に点を均等に配置します。

# 詳細

点は [`generate_N_equally_spaced_points(num_points::Int, e::Ellipse; start_point_shift::Float64=rand())`](@ref) と同様の方法でサンプリングされますが、点の間隔はパラメータ `sqrt_distortion` に依存します。もし `sqrt_distortion == 1.0` であれば、これらの点は弧長に関して均等に配置されます。もし `sqrt_distortion == 0.0` であれば、これらの点は楕円の x および y の位置に関するパラメトリック方程式のパラメータ `t` に関して均等に配置されます（[`x_parametric_equation(t::T, e::Ellipse) where T<:Float64`](@ref) および [`y_parametric_equation(t::T, e::Ellipse) where T<:Float64`](@ref)）。このパラメータを `0.0` と `1.0` の間で変化させることで、これらの二つの極端な間のすべての間隔を得ることができます。

この関数を使用する影響は、`sqrt_distortion < 1.0` のすべての値に対して、生成された点が楕円の主軸の頂点周辺により集まることです（すなわち、最も曲率の大きい領域）。この集まりの強さは `sqrt_distortion` が `0.0` に近づくにつれて増加します。集まりの強さは、主軸と副軸の半径の相対的な大きさにも依存します。主軸と副軸が同じ半径を持つ場合、楕円は円となり、`sqrt_distortion` の値に関係なく集まりは観察されません。主軸の半径の大きさが副軸の半径に対して増加するにつれて、集まりの強さは増加します。

この効果は、楕円を出発点として新しいレベルセットを見つける際に価値があります（それは楕円である可能性があります）。もし、生成された各点で出発楕円から接線方向に押し出して新しいレベルセットを見つけようとする場合、最も速く発散する点は最も曲率の大きい領域に位置します。生成された点が弧長に関して均等に配置されている場合、新しいレベルセットは出発楕円の主軸にほぼ平行な領域でよく定義される可能性が高いですが、他のすべての領域では定義が不十分です。したがって、集まりの効果は新しいレベルセットをより良く定義するのに役立ちます。

この関数は、新しい楕円 `e_new` を定義することによって機能します。`e_new` の副軸半径は供給された楕円の副軸半径と等しく (`e_new.b == e.b`)、主軸半径は供給された楕円 `e` の主軸および副軸半径とパラメータ `sqrt_distortion` の関数として定義されます。すなわち、`e_new.a == e.b + sqrt_distortion^2 * (e.a - e.b)` です。`e_new` は `e` の内部にあり、パラメータ `sqrt_distortion` ∈ [0.0,1.0] を使用して円と `e` の間で変化させることができます。`e_new` を定義した後、弧長に関して `num_points` を均等に配置する角度パラメータ `t_vector` を決定し、その後 `t_vector` の要素によってパラメータ化された `e` 上の点を見つけます。 ```
