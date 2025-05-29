MolecularBoxには3つの型パラメータがあります：  

  * V: StaticArraysパッケージで実装された不変ベクトル
  * N: 次元の数
  * P: どの次元が周期的であるかを示すブール値のタプル

MolecularBoxから継承する具体的な型は、2つのフィールドを実装する必要があります：vectorsとlengths   si(::Box)
