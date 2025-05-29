```
ssim_loss(x, y, kernel=ssim_kernel(x); peakval=1, crop=true, dims=:)
```

`1 - ssim(x, y)`を計算し、勾配降下法での損失関数として使用するのに適しています。トレーニングを高速化するために、カーネルを保存して再利用することをお勧めします。例えば、

```julia
kernel = ssim_kernel(Float32, 2) |> gpu
# または、より高速な計算のために
# kernel = ones(Float32, 5, 5, 1, num_channels) |> gpu

for (x, y) in dataloader
    x, y = (x, y) .|> gpu
    grads = gradient(model) do m
        x̂ = m(y)
        ssim_loss(x, x̂, kernel)
    end
    # モデルを更新 ...
end
```

SSIMおよび上記の引数の詳細な説明については[`ssim`](@ref)を参照してください。また、[`ssim_loss_fast`](@ref)も参照してください。
