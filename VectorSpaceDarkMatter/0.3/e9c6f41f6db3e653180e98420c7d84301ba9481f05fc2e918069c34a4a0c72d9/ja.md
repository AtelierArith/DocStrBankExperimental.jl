```
f_uSph(f::Function; z_even=false, phi_even=false, 
    phi_cyclic=1, phi_symmetric=false, center_Z2=false)
```

関数 $f(u, \theta, \phi)$ に装飾を追加する構造体で、`ProjectF` に関数のさまざまな特性を伝え、積分を高速化します。

`z_even` : (boolean) `f_uSph(x,y,z)` = `f_uSph(x,y,-z)` である場合。$(\ell+m)$ が奇数の場合、$\langle \ell m | f \rangle = 0$ であることを示します。

`phi_even` : (boolean) `f_uSph(u,theta,phi)` = `f_uSph(u,theta,-phi)` である場合。$m < 0$ の場合、$\langle \ell m | f \rangle$ = 0 であることを示します。

`phi_cyclic` : (integer) `f_uSph(u,theta,phi)` = `f_uSph(u,theta,phi + 2*pi/n)` である場合。

`phi_symmetric` : (boolean) `f_uSph(u,theta)` が `phi` に依存しない場合。

`center_Z2` : (boolean) $f(\vec{u}) = f(-\vec{u})$ が中心反転に対して対称である場合。$\ell$ が奇数の場合、$\langle \ell m | f \rangle = 0$ であることを示します。
