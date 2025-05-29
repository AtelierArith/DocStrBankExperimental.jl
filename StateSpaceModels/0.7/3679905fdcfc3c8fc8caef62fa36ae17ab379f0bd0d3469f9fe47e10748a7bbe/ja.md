```
UnobservedComponents(
    y::Vector{Fl}; 
    X::Matrix{Fl} = zeros(Fl, length(y), 0),
    trend::String = "local level",
    seasonal::String = "no"
    cycle::String = "no"
) where Fl
```

トレンド/レベル、季節成分、サイクル成分を持つことができる未観測成分モデルです。各成分は文字列で指定する必要があり、モデルに成分が不要な場合は、キーワード引数として「no」という文字列を渡すことができます。

これらのモデルは一般的な形を取ります。

$$
\begin{gather*}
    \begin{aligned}
    y_t = \mu_t + \gamma_t + c_t + \varepsilon_t
    \end{aligned}
\end{gather*}
$$

ここで、$y_t$は時刻$t$における観測ベクトル、$\mu_t$はトレンド成分、$\gamma_t$は季節成分、$c_t$はサイクル、$\varepsilon_t$は不規則成分を指します。これらの成分のモデリングの詳細は以下に示します。

### **トレンド**

トレンド成分は多くの異なる方法でモデル化できます。通常、傾き成分がない場合はレベルと呼ばれます。モデリングオプションは、例として`trend = "local level"`のように表現できます。

  * ローカルレベル

文字列: `"local level"`

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  \mu_{t} + \varepsilon_{t} \quad \varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \mu_{t+1} &= \mu_{t} + \eta_{t} \quad \eta_{t} \sim \mathcal{N}(0, \sigma^2_{\eta})\\
    \end{aligned}
\end{gather*}
$$

  * ランダムウォーク

文字列: `"random walk"`

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  \mu_{t}\\
        \mu_{t+1} &= \mu_{t} + \eta_{t} \quad \eta_{t} \sim \mathcal{N}(0, \sigma^2_{\eta})\\
    \end{aligned}
\end{gather*}
$$

  * ローカルリニアトレンド

文字列: `"local linear trend"`

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  \mu_{t} + \varepsilon_{t} \quad &\varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \mu_{t+1} &= \mu_{t} + \nu_{t} + \xi_{t} \quad &\xi_{t} \sim \mathcal{N}(0, \sigma^2_{\xi})\\
        \nu_{t+1} &= \nu_{t} + \zeta_{t} \quad &\zeta_{t} \sim \mathcal{N}(0, \sigma^2_{\zeta})\\
    \end{aligned}
\end{gather*}
$$

  * スムーストレンド

文字列: `"smooth trend"`

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  \mu_{t} + \varepsilon_{t} \quad &\varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \mu_{t+1} &= \mu_{t} + \nu_{t}\\
        \nu_{t+1} &= \nu_{t} + \zeta_{t} \quad &\zeta_{t} \sim \mathcal{N}(0, \sigma^2_{\zeta})\\
    \end{aligned}
\end{gather*}
$$

**季節成分**

季節成分は次のようにモデル化されます。

$$
\begin{gather*}
    \begin{aligned}
    \gamma_t = - \sum_{j=1}^{s-1} \gamma_{t+1-j} + \omega_t \quad \omega_t \sim N(0, \sigma^2_\omega)
    \end{aligned}
\end{gather*}
$$

周期性（季節の数）はsであり、定義的な特徴は（誤差項なしで）季節成分が1つの完全なサイクルを通じてゼロに合計されることです。誤差項を含めることで、季節効果が時間とともに変動することができます。モデリングオプションは、`"deterministic"`または`"stochastic"`という形で表現でき、周期性は文字列の中の数値として表現できます。すなわち、`seasonal = "stochastic 12"`のようになります。

**サイクル成分**

サイクル成分は次のようにモデル化されます。

$$
\begin{gather*}
    \begin{aligned}
        c_{t+1} &= \rho_c \left(c_{t} \cos(\lambda_c) + c_{t}^{*} \sin(\lambda_c)\right) \quad & \tilde\omega_{t} \sim \mathcal{N}(0, \sigma^2_{\tilde\omega})\\
        c_{t+1}^{*} &= \rho_c \left(-c_{t} \sin(\lambda_c) + c_{t}^{*} \sin(\lambda_c)\right) \quad &\tilde\omega^*_{t} \sim \mathcal{N}(0, \sigma^2_{\tilde\omega})\\
    \end{aligned}
\end{gather*}
$$

サイクル成分は、季節成分によって捉えられるよりもはるかに長い時間枠でのサイクル効果を捉えることを目的としています。パラメータ$\lambda_c$はサイクルの周波数であり、最大尤度法によって推定されます。誤差項を含めることで、サイクル効果が時間とともに変動することができます。モデリングオプションは、`"deterministic"`または`"stochastic"`という形で表現でき、減衰効果は文字列として表現できます。すなわち、`cycle = "stochastic"`、`cycle = "deterministic"`または`cycle = "stochastic damped"`のようになります。

UnobservedComponentsモデルには、いくつかの専用のプロットレシピがあります。詳細は[Visualization](@ref)を参照してください。

# 参考文献

  * Durbin, James, & Siem Jan Koopman. Time Series Analysis by State Space Methods: Second Edition.  Oxford University Press, 2012

```
