Minimize `0.5*x'*H*x + x'*g`  s.t. lower<=x<=upper

inputs:      `H`            - positive definite matrix   (n * n)      `g`            - bias vector                (n)      `lower`        - lower bounds               (n)      `upper`        - upper bounds               (n)

optional inputs:      `x0`           - initial state              (n)      `options`      - see below                  (7)

outputs:      `x`            - solution                   (n)      `result`       - result type (roughly, higher is better, see below)      `Hfree`        - subspace cholesky factor   (n*free * n*free)      `free`         - set of free dimensions     (n)
