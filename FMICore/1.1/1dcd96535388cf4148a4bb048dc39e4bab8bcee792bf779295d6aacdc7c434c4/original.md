Types of dependency:

  * `fmi2DependencyKindDependent`: no particular structure, f(v)
  * `fmi2DependencyKindConstant`: constant factor, c*v (for Real valued variables only)
  * `fmi2DependencyKindFixed`: tunable factor, p*v (for Real valued variables only)
  * `fmi2DependencyKindTunable` [ToDo]
  * `fmi2DependencyKindDiscrete` [ToDo]

Source: FMI2.0.3 Spec for fmi2VariableDependency [p.60] 
