```
DoG(repsilon)
```

Distance over gradient (DoG[^IHC2023]) optimizer. It's only parameter is the initial guess of the Euclidean distance to the optimum repsilon. The original paper recommends $ 10^{-4} ( 1 + \lVert \lambda_0 \rVert ) $, but the default value is $ 10^{-6} $.

# Parameters

  * `repsilon`: Initial guess of the Euclidean distance between the initial point and the optimum. (default value: `1e-6`)
