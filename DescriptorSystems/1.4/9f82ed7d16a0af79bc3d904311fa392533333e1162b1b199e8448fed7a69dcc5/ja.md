```
glcf(sys; smarg, sdeg, evals, mindeg = false, mininf = false, fast = true, 
     atol = 0, atol1 = atol, atol2 = atol, atol3 = atol, rtol = n*ϵ) -> (sysn, sysm)
```

記述子システム `sys = (A-λE,B,C,D)` に対して、安定かつ適切な左互素因子分解の因子 `sysn = (An-λEn,Bn,Cn,Dn)` と `sysm = (Am-λEm,Bm,Cm,Dm)` を計算します。もし `sys`、`sysn` および `sysm` がそれぞれ伝達関数行列 `G(λ)`、`N(λ)` および `M(λ)` を持つ場合、`G(λ) = inv(M(λ))*N(λ)` となり、`N(λ)` と `M(λ)` は適切かつ安定な伝達関数行列です。結果として得られる行列ペア `(An,En)` と `(Am,Em)` は（一般化された）シュール形式になります。極の安定性領域 `Cs` は、安定性マージンのキーワード引数 `smarg` によって定義され、次のようになります：連続時間システム `sys` に対して、`Cs` は実部が最大 `smarg` である複素数の集合であり、離散時間システム `sys` に対して、`Cs` は絶対値が最大 `smarg < 1` である複素数の集合（すなわち、原点を中心とした半径 `smarg` の円の内部）です。`smarg` が指定されていない場合、使用されるデフォルト値は、連続時間システムに対して `smarg = -sqrt(eps)`、離散時間システムに対して `smarg = 1-sqrt(eps)` です。

キーワード引数 `sdeg` は、因子の指定された固有値に対する安定性の度合いを指定します。`sdeg` と `smarg` の両方が指定されていない場合、使用されるデフォルト値は、連続時間システムに対して `sdeg = -0.05`、離散時間システムに対して `sdeg = 0.95` です。一方、`smarg` が指定されている場合、`sdeg = smarg` が使用されます。

キーワード引数 `evals` は、因子のための有限の望ましい固有値のセットを含む実数または複素数のベクトルです。実データを持つシステムの場合、`evals` は結果の因子も実数であることを保証するために自己共役複素数のセットでなければなりません。

`mindeg = false` の場合、両方の因子 `sysn` と `sysm` は同じ次数の記述子実現を持ち、`An = Am`、`En = Em` および `Cn = Cm` となります。`mindeg = true` の場合、`sysm` の実現は最小です。`sysm` の（有限の）極の数は、`sys` の不安定な有限極の数に等しくなります。

`mininf = false` の場合、`An-λEn` と `Am-λEm` は単純な無限固有値を持つ可能性があります。`mininf = true` の場合、`An-λEn` と `Am-λEm` は単純な無限固有値を持ちません。単純な無限固有値の除去には行列の逆行列が関与することに注意してください。

キーワード引数 `atol1`、`atol2`、`atol3` および `rtol` は、それぞれ `A` の非ゼロ要素に対する絶対許容誤差、`E` の非ゼロ要素に対する絶対許容誤差、`C` の非ゼロ要素に対する絶対許容誤差、および `A`、`E` および `C` の非ゼロ要素に対する相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `ϵ` は `A` の要素型のマシンイプシロンで、`n` はシステム `sys` の次数です。キーワード引数 `atol` は、`atol1 = atol`、`atol2 = atol`、`atol3 = atol` を同時に設定するために使用できます。

`A-λE` の有限および無限固有値の予備的な分離は、`fast = true` の場合は列ピボットを用いたランクを明らかにするQR分解に基づくランク決定を使用して、`fast = false` の場合はより信頼性の高いSVD分解を使用して行われます。

*メソッド:*  [2] の手続き GRCF の双対が使用され、これは無限極に対処するための [1] の再帰的因子分解アプローチの拡張を表します。すべての無限固有値は有限の実値に割り当てられます。`evals` が指定されていないか、十分な数の実値を含まない場合、`A-λE` の無限固有値の一部またはすべてが `sdeg` で指定された値に割り当てられます。ペア `(An,En)` と `(Am,Em)` は、両方の `An` と `Am` が準上三角行列であり、`En` と `Em` が両方とも上三角行列または両方ともUniformScalingsである*一般化されたシュール形式*を生成します。

*参考文献:*

[1] A. Varga. Computation of coprime factorizations of rational matrices.     Linear Algebra and Its Applications, vol. 271, pp.88-115, 1998.

[2] A. Varga. On recursive computation of coprime factorizations of rational matrices.      arXiv:1703.07307, https://arxiv.org/abs/1703.07307, 2020. (Linear Algebra and Its Applicationsに掲載予定)
