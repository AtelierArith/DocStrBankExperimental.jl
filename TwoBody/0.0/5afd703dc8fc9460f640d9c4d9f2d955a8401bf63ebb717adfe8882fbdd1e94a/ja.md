`solve(hamiltonian::Hamiltonian, method::FiniteDifferenceMethod; perturbation=Hamiltonian(), info=4, nₘₐₓ=4)`

このメソッドは、有限差分近似を用いてスパース行列として離散化されたハミルトニアンの固有値問題を解きます。

$$
\pmb{H} \pmb{\psi} = E \pmb{\psi}.
$$

固有値 $E$ は正確なエネルギーの近似であり、固有ベクトル $\pmb{\psi}$ はグリッドの点における正確な波動関数 $\psi(r)$ の近似値のベクトルです。

$$
\pmb{\psi}
=
\left(\begin{array}{c}
  \psi(r_1) \\
  \psi(r_2) \\
  \psi(r_3) \\
  \vdots \\
\end{array}\right).
$$
