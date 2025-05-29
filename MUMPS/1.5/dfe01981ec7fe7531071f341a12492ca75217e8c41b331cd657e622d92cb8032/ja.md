```
module MUMPS
```

MUMPS 5.8.0の並列直接ソルバーCライブラリとの低レベルインターフェースと、MUMPSの一般的な使用法のための便利なラッパーの両方を提供します。

中心的な作業は`Mumps`構造体によって行われ、これはMUMPSで使用される内部構造を反映しています。このオブジェクトに対して直接操作を行い、関数[`invoke_mumps!`](@ref)を介してMumpsに渡すことができます。この操作モードは、MUMPSマニュアルに記載されているように、ユーザーに完全な制御を提供しますが、安全でない操作を露出させるため、注意が必要です。

より便利なのは、関数[`mumps_solve`](@ref)、[`mumps_factorize`](@ref)、[`mumps_det`](@ref)、[`mumps_schur_complement`](@ref)、および[`mumps_select_inv`](@ref)の使用で、これらはすべてミューテーション対応の対応関数（例えば、[`mumps_solve!`](@ref)）を持っています。これらは行列と右辺を直接受け取ることができるため、例えば、方程式`A*x=y`は、Baseで`x=A\y`または`LinearAlbegra.ldiv!(x,A,y)`によって解かれ、MUMPSでは`x=mumps_solve(A,y)`または`mumps_solve!(x,A,y)`として解くことができます。

このパッケージは、Base.det、Base.\、LinearAlgebra.ldiv!およびLinearAlgebra.invを拡張して、mumpsオブジェクトと連携できるようにします。

低レベルインターフェースを使用していない限り、`JOB`パラメータを手動で設定することは推奨しません。これは安全でない操作につながる可能性があります。

目標は、高度なユーザーにMUMPSへの低レベルアクセスを提供しつつ、一般のユーザーにはMUMPSが提供するほとんどすべてにアクセスできる安全な関数を提供することです。
