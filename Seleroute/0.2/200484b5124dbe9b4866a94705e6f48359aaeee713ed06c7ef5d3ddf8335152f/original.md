For robust and oblivious uncertainties, this package natively offers multiple algorithm choices:

  * `Automatic`: let the package decide which algorith to use
  * `CuttingPlane`: use an iterative cutting-plane algorithm (solves many small problems)
  * `DualReformulation`: use a dual-reformulation of the uncertainty set (solves one large problem)

For other types of uncertainty, use the value `Automatic`.
