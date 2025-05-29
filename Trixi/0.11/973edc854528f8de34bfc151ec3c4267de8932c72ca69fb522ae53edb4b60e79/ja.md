```
flux_nonconservative_powell_local_symmetric(u_ll, u_rr,
                                            orientation::Integer,
                                            equations::IdealGlmMhdEquations2D)
```

非対称の二点フラックスは、Powellの非保守（ソース）項と、[`IdealGlmMhdEquations2D`](@ref)のGLM乗数に関連するガリレイ非保守項を離散化します。

この実装は、局所的かつ対称的な部分の積として書くことができる非保守項を使用します。これは、適合メッシュに対するBohmらの非保守フラックス[`flux_nonconservative_powell`](@ref)と同等ですが、非適合メッシュでは異なる結果をもたらします(!)。曲線メッシュでは、この定式化は、[`flux_nonconservative_powell`](@ref)で使用される平均的なものと比較して、局所的な法線方向を適用します。

同じ名前の他の二つのフラックス関数は、非保守*タイプ引数のタイプに基づいて、非保守フラックスの局所部分または対称部分のいずれかを返し、複数のディスパッチを使用します。これらは、dg*2d*subcell*limiters.jlでサブセルフラックスを計算するために使用されます。

## 参考文献

  * Rueda-Ramírez, Gassner (2023). A Flux-Differencing Formula for Split-Form Summation By Parts Discretizations of Non-Conservative Systems. https://arxiv.org/pdf/2211.14009.pdf.
