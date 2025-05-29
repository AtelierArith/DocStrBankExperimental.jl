```
ssim_loss(x, y, kernel=ssim_kernel(x); peakval=1, crop=true, dims=:)
```

Computes `1 - ssim(x, y)`, suitable for use as a loss function with gradient descent. For faster training, it is recommended to store a kernel and reuse it, ex.,

```julia
kernel = ssim_kernel(Float32, 2) |> gpu
# or alternatively for faster computation
# kernel = ones(Float32, 5, 5, 1, num_channels) |> gpu

for (x, y) in dataloader
    x, y = (x, y) .|> gpu
    grads = gradient(model) do m
        x̂ = m(y)
        ssim_loss(x, x̂, kernel)
    end
    # update the model ...
end
```

See [`ssim`](@ref) for a detailed description of SSIM and the above arguments. See also [`ssim_loss_fast`](@ref).
