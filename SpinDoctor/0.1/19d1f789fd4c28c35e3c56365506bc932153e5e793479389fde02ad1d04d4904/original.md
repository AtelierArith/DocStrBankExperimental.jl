```
solve(problem::HADC, gradient::ScalarGradient, odesolver = QNDF();
    abstol = 1e-6,
    reltol = 1e-4,
)
```

Compute the ADC using a homogenized ADC model (HADC). This is currently only implemented for scalar gradients.
