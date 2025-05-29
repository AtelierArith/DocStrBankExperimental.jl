The `hazard` for `JointSurvivalModel` calculates the hazard according to the formulation $h(t) = h_0(t) \exp\left(\gamma' \cdot L(M(t)) + \beta' \cdot x \right)$ described in the documentation of `JointSurvivalModel`

# Example

`my_joint_model = JointSurvivalModel(identity, 0.01, identity) hazard(my_joint_model, 10)``
