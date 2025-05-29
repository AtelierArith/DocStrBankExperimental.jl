```
struct TransientMDEIMReduction{A,R<:Reduction{A,EuclideanNorm}} <: AbstractMDEIMReduction{A}
  reduction::R
  combine::Function
end
```

遷移問題に使用されるMDEIM構造体。フィールド`combine`は、さまざまなヤコビアンに関連する削減をスマートにグループ化するために使用される関数です（一般的に、遷移問題では1つ以上のヤコビアンがあります）。例えば、次の常微分方程式（ODE）を考えます。

$$
\tfrac{du}{dt} - \nu \Delta u = f \ \ \text{in} \ \ Ω \times [0,T]
$$

初期/境界条件に従います。空間にFE離散化を適用し、時間に`θ`法を適用すると、空間-時間系が得られます。

$$
A_{\theta} u_{\theta} = f_{\theta}
$$

ここで、

$$
A_{\theta} = \begin{bmatrix}
A_1 + M / (\theta \Delta t) & & & & & \\
- M / (\theta \Delta t) & A_2 + M / (\theta \Delta t) & & & & \\
& - M / (\theta \Delta t) & A_3 + M / (\theta \Delta t) & & & \\
& & \ddots & \ddots & & \\
& & & & - M / (\theta \Delta t) & A_n + M / (\theta \Delta t)
\end{bmatrix};
$$

$$
u_{\theta} = \left[(1-\theta)u_0 + \theta u_1, \hdots, (1-\theta)u_{n-1} + \theta u_n\right]^T;
$$

$$
f_{\theta} = \left[f_1, \hdots, f_n\right]^T;
$$

$$
A_k = A(t_{k-1} + \theta \Delta t);
$$

$$
f_k = f(t_{k-1} + \theta \Delta t).
$$

注意：$A_{\theta}$を$u_{\theta}$で掛ける代わりに、$\tilde{A}_{\theta}$を$u$で掛けます。ここで、

$$
\tilde{A}_{\theta} = tridiag((1-\theta)A_{k-1} - M / \Delta t, \theta A_k + M / \Delta t, 0).
$$

今、状態変数$u$に関連するスナップショットを削減することによって得られる空間基底と時間基底をそれぞれ$\Phi$と$\Psi$で示します。空間-時間系のガレルキン射影は$\hat{A}_{\theta}\hat{u} = \hat{f}_{\theta}$に等しく、ここで$\hat{u}$は未知数であり、

$$
\begin{align*}
\hat{A}_{\theta} &= \sum\limits_{k=1}^{n-1} ( (1-θ) \Phi^T A_k \Phi - \Phi^T M \Phi / \Delta t) \otimes \Psi[k-1,:]^T \Psi[k,:]
  + \sum\limits_{k=1}^n (\theta \Phi^T A_k \Phi + \Phi^T M \Phi / \Delta t) \otimes \Psi[k,:]^T \Psi[k,:] \\
  &= \theta A_{backwards} + (1-\theta)A_{forwards} + (M_{backwards} + M_{forwards}) / \Delta t \\
\hat{f}_{\theta} &= \sum\limits_{k=1}^n \Phi^T f_k \otimes \Psi[k,:]
\end{align*}
$$

$$
\hat{A}_{\theta}
$$

の表現は、より一般的な形で書くことができることに注意してください。

$$
\hat{A}_{\theta} = combine_A(A_{backwards},A_{forwards}) + combine_M(M_{backwards},M_{forwards}),
$$

ここで、combine*Aとcombine*MはAとMに特有の2つの関数です：

$$
\begin{align*}
combine_A(x,y) &= \theta y + (1-\theta)y \\
combine_M(x,y) &= (x - y) / \Delta t
\end{align*}
$$

任意の時間進行スキームについても同様のことが言えます。これが関数`combine`の意味です。$p$個の補間点を持つ時間進行の場合（例えば、$\theta$法の場合、$p = 2$）、`combine`関数は$p$個の引数を受け入れる必要があります。
