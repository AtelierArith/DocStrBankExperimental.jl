```
rmca(
     r = 1, K = 1e4, A = 1e3,
     b = 1e-3, c = 1, m = 0.8,
     V = 100, σ = 0.01,
     N₀ = 3000, P₀ = 4, t₀ = 0.0,
     δt = 0.01,
     times=range(start=0,stop=500,step=0.2)
   )
```

## Parameters

  * r: intrinsic growth rate of prey
  * K: carrying capacity for prey
  * A: half-saturation prey density
  * c: predator foraging rate
  * b: predator yield (predators born per prey item killed)
  * m: predator death rate
  * V: system size
  * σ: measurement noise magnitude
  * N₀, P₀: initial densities
  * t₀: zero-time
  * δt: Euler stepsize
  * times: vector of observation times

## Observables

  * n: prey density
  * p: predator density

## State variables

  * $X = \log(N)$
  * $Y = \log(P)$

## Details

`rmca` returns a *PompObject* containing simulated data from a Rosenzweig-MacArthur model implemented as an Itô diffusion. Specifically, if $N$ and $P$ are prey and predator densities, respectively, then $dN = dG - dC - dS$ and $dP = b dS - dM$, where

$$
\begin{aligned}
dG &= r N dt + \sqrt{\frac{1}{V} r N} dW_1 \\
dC &= \frac{r N^2}{K} dt + \sqrt{\frac{1}{V} \frac{r N^2}{K}} dW_2 \\
dS &= \frac{c N P}{1+N/A} dt + \sqrt{\frac{1}{V} \frac{c N P}{1+N/A}} dW_3 \\
dM &= m P dt + \sqrt{\frac{1}{V} m P} dW_4 \\
\end{aligned}
$$

Here, the $dW_i$ are increments of independent standard Wiener processes. Thus, the process noise scales demographically. Specifically, the system size, $V$, converts the densities $N$, $P$ into numbers. It controls the relative magnitude (coefficient of variation) of the demographic process noise. Moreover, $V$ determines a lower threshold on the population sizes, such that if ever $N V < 1$ or $P V < 1$, the population is taken to be extinct. Otherwise, it plays no role in the dynamics. The measurement error is assumed to scale environmentally:

$$
\begin{aligned}
n &\sim \mathrm{LogNormal}(\log{N},\sigma) \\
p &\sim \mathrm{LogNormal}(\log{P},\sigma) \\
\end{aligned}
$$

Note that, in the limit $V\to\infty$, the Itô diffusion becomes the ordinary differential equation

$$
\begin{aligned}
\frac{dN}{dt} &= r N \left(1-\frac{N}{K}\right) - \frac{c N P}{1+N/A} \\
\frac{dP}{dt} &= \frac{b c N P}{1+N/A} - m P \\
\end{aligned}
$$

which is the classical Rosenzweig-MacArthur model.

In this system, the predator is inviable unless $R = \frac{bcA}{m} > 1$. Even if the predator is viable, the environment is too impoverished to support predators unless $R>1+\frac{A}{K}$. If the environment is rich enough, and if moreover $R>\frac{1+\frac{A}{K}}{1-\frac{A}{K}}$, then the nontrivial equilibrium of the system is unstable. For the default parameters, we have $R = 1.25$ and $\frac{A}{K} = 0.1$, so the latter condition holds.
