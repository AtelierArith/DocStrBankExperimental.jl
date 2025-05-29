```
GAN(dat::Union{Array,PyObject}, generator::Function, discriminator::Function,
loss::Union{Missing, Function}=missing; latent_dim::Union{Missing, Int64}=missing,
    batch_size::Int64=32)
```

GANインスタンスを作成します。

  * `dat` $\in \mathbb{R}^{n\times d}$ はGANのトレーニングデータで、$n$はトレーニングデータの数、$d$はトレーニングデータごとの次元です。
  * `generator`$:\mathbb{R}^{d'} \rightarrow \mathbb{R}^d$ は生成器関数で、$d'$は隠れ次元です。
  * `discriminator`$:\mathbb{R}^{d} \rightarrow \mathbb{R}$ は識別器関数です。
  * `loss` は損失関数です。例としては [`klgan`](@ref), [`rklgan`](@ref), [`wgan`](@ref), [`lsgan`](@ref) を参照してください。
  * `latent_dim` (デフォルト=$d$, 出力次元と同じ) は潜在次元です。
  * `batch_size` (デフォルト=32) はトレーニング時のバッチサイズです。

# 例: GANの構築

```julia
dat = rand(10000,10)
generator = (z, gan)->10*z
discriminator = (x, gan)->sum(x)
gan = GAN(dat, generator, discriminator, "wgan_stable")
```

# 例: ガウス乱数変数の学習

```julia
using ADCME 
using PyPlot
using Distributions
dat = randn(10000, 1) * 0.5 .+ 3.0
function gen(z, gan)
    ae(z, [20,20,20,1], "generator_$(gan.ganid)", activation = "relu")
end
function disc(x, gan)
    squeeze(ae(x, [20,20,20,1], "discriminator_$(gan.ganid)", activation = "relu"))
end
gan = GAN(dat, gen, disc, g->wgan_stable(g, 0.001); latent_dim = 10)

dopt = AdamOptimizer(0.0002, beta1=0.5, beta2=0.9).minimize(gan.d_loss, var_list=gan.d_vars)
gopt = AdamOptimizer(0.0002, beta1=0.5, beta2=0.9).minimize(gan.g_loss, var_list=gan.g_vars)
sess = Session(); init(sess)
for i = 1:5000
    batch_x = rand(1:10000, 32)
    batch_z = randn(32, 10)
    for n_critic = 1:1
        global _, dl = run(sess, [dopt, gan.d_loss], 
                feed_dict=Dict(gan.ids=>batch_x, gan.noise=>batch_z))
    end
    _, gl, gm, dm, gp = run(sess, [gopt, gan.g_loss, 
        gan.STORAGE["g_grad_magnitude"], gan.STORAGE["d_grad_magnitude"], 
        gan.STORAGE["gradient_penalty"]],
        feed_dict=Dict(gan.ids=>batch_x, gan.noise=>batch_z))
    mod(i, 100)==0 && (@info i, dl, gl, gm, dm, gp)
end

hist(run(sess, squeeze(rand(gan,10000))), bins=50, density = true)
nm = Normal(3.0,0.5)
x0 = 1.0:0.01:5.0
y0 = pdf.(nm, x0)
plot(x0, y0, "g")
```
