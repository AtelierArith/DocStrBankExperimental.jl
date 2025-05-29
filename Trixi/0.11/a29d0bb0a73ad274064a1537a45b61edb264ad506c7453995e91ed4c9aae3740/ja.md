```
splitting_vanleer_haenel(u, orientation::Integer,
                         equations::CompressibleEulerEquations1D)
splitting_vanleer_haenel(u, which::Union{Val{:minus}, Val{:plus}}
                         orientation::Integer,
                         equations::CompressibleEulerEquations1D)
```

バン・ルーアによる圧縮性オイラーのフラックスの分割。この分割は、エネルギーフラックスがエンタルピーを使用するハーネルらによる再定式化をさらに含んでいます。圧力の分割は、対流項の分割とは独立しています。そのため、文献には多くの圧力分割が提案されています。私たちは、実際に最も堅牢であることが証明されたリウとステッフェンによって提案された「p4」バリアントを実装します。

「マイナス」（負の軸方向に進む波に関連）と「プラス」（正の軸方向に進む波に関連）のフラックスのタプルを返します。フラックスのうちの1つだけが必要な場合は、引数 `which` を `Val{:minus}()` または `Val{:plus}()` に設定した関数シグネチャを使用してください。

!!! warning "実験的実装（アップウィンドSBP）"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。


## 参考文献

  * Bram van Leer (1982) Flux-Vector Splitting for the Euler Equation [DOI: 10.1007/978-3-642-60543-7_5](https://doi.org/10.1007/978-3-642-60543-7_5)
  * D. Hänel, R. Schwane and G. Seider (1987) On the accuracy of upwind schemes for the solution of the Navier-Stokes equations [DOI: 10.2514/6.1987-1105](https://doi.org/10.2514/6.1987-1105)
  * Meng-Sing Liou and Chris J. Steffen, Jr. (1991) High-Order Polynomial Expansions (HOPE) for Flux-Vector Splitting [NASA Technical Memorandum](https://ntrs.nasa.gov/citations/19910016425)
