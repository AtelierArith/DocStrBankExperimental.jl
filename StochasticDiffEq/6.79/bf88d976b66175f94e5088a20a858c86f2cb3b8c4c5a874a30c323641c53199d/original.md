Kloeden, P.E., Platen, E., Numerical Solution of Stochastic Differential Equations. Springer. Berlin Heidelberg (2011)

RKMilCommute: Nonstiff Method An explicit Runge-Kutta discretization of the strong order 1.0 Milstein method for commutative noise problems. Defaults to solving the Ito problem, but RKMilCommute(interpretation=SciMLBase.AlgorithmInterpretation.Stratonovich) makes it solve the Stratonovich problem. Uses a 1.5/2.0 error estimate for adaptive time stepping. Default: ii_approx=IICommutative() does not approximate the Levy area.
