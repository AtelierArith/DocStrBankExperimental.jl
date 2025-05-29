`JointSurvivalModel`の`hazard`は、ドキュメントに記載されている定式化$h(t) = h_0(t) \exp\left(\gamma' \cdot L(M(t)) + \beta' \cdot x \right)$に従ってハザードを計算します。

# 例

`my_joint_model = JointSurvivalModel(identity, 0.01, identity) hazard(my_joint_model, 10)`
