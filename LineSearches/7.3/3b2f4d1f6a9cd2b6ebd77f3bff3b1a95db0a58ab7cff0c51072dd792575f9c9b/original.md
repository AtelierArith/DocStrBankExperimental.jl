`BackTracking` specifies a backtracking line-search that uses a quadratic or cubic interpolant to determine the reduction in step-size. E.g., if f(α) > f(0) + c₁ α f'(0), then the quadratic interpolant of f(0), f'(0), f(α) has a minimiser α' in the open interval (0, α). More strongly, there exists a factor ρ = ρ(c₁) such that α' ≦ ρ α.

This is a modification of the algorithm described in Nocedal Wright (2nd ed), Sec. 3.5.
