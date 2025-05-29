```
create_kernel(seq, x, X, g)
```

If data vector of real values is provided, SVD is performed on the kernel, and the output is a "svd*kernel*struct" instead.

If data vector is complex, the SNR is calculated and the SVD is automatically truncated accordingly, to remove the "noisy" singular values.
