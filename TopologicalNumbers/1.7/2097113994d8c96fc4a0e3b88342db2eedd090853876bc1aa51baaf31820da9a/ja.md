```
pfaffian_schur(A::AbstractMatrix{T}; overwrite_a=false) where {T<:Real}
```

実数反対称行列のPfaffianをシュール分解を用いて計算します。（原則としてヘッセンベルグの方が速いですが、scipy-0.8がscipy.linalg.hessenberg()のパフォーマンスを台無しにしました）。

この関数は行列Aの斜対称性を利用せず、FORTRANでコーディングされたLAPACKルーチンを使用しているため、Pythonよりも速くなっています。その結果、pfaffian_schurはpfaffian()よりもわずかに遅いだけです。
