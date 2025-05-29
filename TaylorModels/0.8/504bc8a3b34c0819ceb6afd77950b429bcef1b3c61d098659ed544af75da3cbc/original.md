rpa(g::Function, tmf::TaylorModel1)    rpa(g::Function, tmf::RTaylorModel1)    rpa(g::Function, tmf::TaylorModelN)

Rigurous polynomial approximation (RPA) for the function `g` using the Taylor Model with absolute/relative remainder `tmf`. The bound is computed exploiting monotonicity if possible, otherwise, it uses Lagrange bound.
