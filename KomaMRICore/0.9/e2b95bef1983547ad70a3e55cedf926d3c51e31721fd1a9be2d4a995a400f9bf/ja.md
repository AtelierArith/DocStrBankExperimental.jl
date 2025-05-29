```
s = Q(φ, nxy, nz)
```

スピノル回転行列。回転軸 n=(nx, ny, nz) に対して角度 `φ` の反時計回りの回転。

Pauly, J., Le Roux, P., Nishimura, D., & Macovski, A. (1991). Shinnar-Le Roux 選択的励起パルス設計アルゴリズムのパラメータ関係 (NMR 画像)。IEEE Transactions on Medical Imaging, 10(1), 53-65. doi:10.1109/42.75611

$$
\varphi=-\gamma\Delta t\sqrt{\left|B_{1}\right|^{2}+\left(\boldsymbol{G}\cdot\boldsymbol{x}
\right)^{2}}=-\gamma\Delta t\left\Vert \boldsymbol{B}\right\Vert
$$

$$
\boldsymbol{n}=\boldsymbol{B}/\left\Vert \boldsymbol{B}\right\Vert
$$

# 引数

  * `φ`: (`::Real`, `[rad]`) φ 角
  * `nxy`: (`::Real`) nxy 因子
  * `nz`: (`::Real`) nz 因子

# 戻り値

  * `s`: (`::Spinor`) `Q` 回転行列を表すスピノル構造体
