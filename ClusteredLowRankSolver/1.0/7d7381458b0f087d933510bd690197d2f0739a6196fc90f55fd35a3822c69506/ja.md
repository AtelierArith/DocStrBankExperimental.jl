```
linearsystem_coefficientmatching(problem::Problem, monomial_basis::Vector{Vector{MPolyRingElem}}; FF=QQ)
```

xを行列変数のベクトル化のvcatとします。この関数は、係数一致から得られる制約が、体FF上でのシステムAx = bによって与えられる行列Aとベクトルbを返します。monomial_basisの各モノミアルに対して1つの制約があります。この機能が動作するためには、問題にSampledMPolyRingElemが含まれていてはいけません。
