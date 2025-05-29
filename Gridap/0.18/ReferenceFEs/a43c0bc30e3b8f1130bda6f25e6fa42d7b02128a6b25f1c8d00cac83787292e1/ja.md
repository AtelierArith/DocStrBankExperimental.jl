```
abstract type ReferenceFE{D} <: GridapType
```

抽象型は、参照有限要素を表します。`D`は基盤となる座標空間の次元です。私たちはCiarletの定義に従います。参照有限要素は、ポリトープ（セルトポロジー）、このポリトープの上にある補間空間の基底（ここでは前基底と呼ばれます）、およびこの空間の双対の基底（すなわち自由度）によって定義されます。この情報から、基底の単純な変更によって形状関数（すなわち自由度に関する標準基底）を計算することができます。さらに、この型には、参照有限要素の補間空間が隣接する要素とどのように「接合」されているかに関する情報もエンコードされています。これは、適合するセル単位の空間を構築するために必要です。

`ReferenceFE`インターフェースは、これらのメソッドをオーバーロードすることによって定義されます：

  * [`num_dofs(reffe::ReferenceFE)`](@ref)
  * [`get_polytope(reffe::ReferenceFE)`](@ref)
  * [`get_prebasis(reffe::ReferenceFE)`](@ref)
  * [`get_dof_basis(reffe::ReferenceFE)`](@ref)
  * [`Conformity(reffe::ReferenceFE)`](@ref)
  * [`get_face_own_dofs(reffe::ReferenceFE,conf::Conformity)`](@ref)
  * [`get_face_own_dofs_permutations(reffe::ReferenceFE,conf::Conformity)`](@ref)
  * [`get_face_dofs(reffe::ReferenceFE)`](@ref)

インターフェースは以下でテストされます：

  * [`test_reference_fe(reffe::ReferenceFE)`](@ref)
