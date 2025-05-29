```
summary_eigenvalues(
        sm::SmallSignalOutput,
)
```

Function to obtain a summary of the eigenvalues of the Jacobian at the operating point. It returns a DataFrame with the most associated state for each eigenvalue, its real and imaginary part, damping and frequency.

# Arguments

  * `sm::SmallSignalOutput` : Small Signal Output object that contains the eigenvalues and participation factors
