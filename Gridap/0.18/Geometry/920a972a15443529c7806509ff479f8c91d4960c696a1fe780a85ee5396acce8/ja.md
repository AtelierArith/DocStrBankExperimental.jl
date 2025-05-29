CartesianDiscreteModel(desc::CartesianDescriptor{D,T,F},                           cmin::CartesianIndex,                           cmax::CartesianIndex)

CartesianDescriptor{D,T,F}によって表される（より大きな）グリッドのサブグリッドを表すCartesianDiscreteModelオブジェクトを構築します。このサブグリッドは、D次元の最小（cmin）および最大（cmax）CartesianIndex識別子によって記述されます。
