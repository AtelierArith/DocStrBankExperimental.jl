```
partial_linearsystem(problem::Problem, sol::DualSolution, columns::Union{DualSolution, Vector{Int}})
```

xを行列変数のベクトル化のvcatとします。Iを列のインデックス集合とします。この関数は、行列A*Iとベクトルb-Axを返します。ここで、Iでインデックス付けされた変数を使用してエラー ベクトルeの制約がA*Ie = b-Axというシステムによって与えられます。
