## モデル

このモデルは時間非依存のシュレーディンガー方程式で記述されます。

$$
  \hat{H} \psi(\theta,\varphi) = E \psi(\theta,\varphi),
$$

およびハミルトニアン

$$
\begin{aligned}
  \hat{H} &= - \frac{\hbar^2}{2\mu} \nabla^2 + V(r), \\
          &= - \frac{\hbar^2}{2I} \left[ \frac{1}{\sin\theta} \frac{\partial}{\partial\theta} \left(\sin\theta \frac{\partial}{\partial\theta}\right) + \frac{1}{\sin^2\theta} \frac{\partial^2}{\partial\phi^2}  \right], \\
          &= \frac{L^2}{2I}
\end{aligned}
$$

ここで、$I=\mu R^2$ は慣性モーメント、$\mu=\left(\frac{1}{m_1}+\frac{1}{m_2}\right)^{-1}$ は二つの粒子の縮退質量、$R$ は二つの粒子間の距離、$L^2$ は角運動量演算子です。パラメータは次の構造体で指定されます。

```
RR = RigidRotor(m₁=1.0, m₂=1.0, R=1.0, ℏ=1.0)
```

$$
m₁
$$

と $m₂$ は二つの粒子の質量、$R$ は距離、$\hbar$ は縮退プランク定数（ディラック定数）です。

## 参考文献

  * [D. A. McQuarrie, J. D. Simon, *Physical chemistry : a molecular approach* (University Science Books, 1997)](https://uscibooks.aip.org/books/physical-chemistry-a-molecular-approach/) p.173, 5.8 剛体回転子のエネルギー準位は $E = \hbar^2 J(J+1) / 2I$
  * [Chemistry Libre Texts](https://chem.libretexts.org/Bookshelves/Physical_and_Theoretical_Chemistry_Textbook_Maps/Physical_Chemistry_(LibreTexts)/05%3A_The_Harmonic_Oscillator_and_the_Rigid_Rotor/5.08%3A_The_Energy_Levels_of_a_Rigid_Rotor)
