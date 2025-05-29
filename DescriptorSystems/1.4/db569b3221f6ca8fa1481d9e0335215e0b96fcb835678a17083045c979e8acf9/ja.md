```
grcfid(sys; mindeg = false, mininf = false, fast = true, offset = sqrt(ϵ), 
       atol = 0, atol1 = atol, atol2 = atol, atol3 = atol, rtol = n*ϵ) -> (sysni, sysmi)
```

記述子システム `sys = (A-λE,B,C,D)` のために、右互素因子分解の因子 `sysni = (Ani-λEni,Bni,Cni,Dni)` と `sysmi = (Ami-λEmi,Bmi,Cmi,Dmi)` を計算します。もし `sys`、`sysni`、および `sysmi` がそれぞれ伝達関数行列 `G(λ)`、`N(λ)`、および `M(λ)` を持つ場合、`G(λ) = N(λ)*inv(M(λ))` となり、`N(λ)` と `M(λ)` は適切で安定な伝達関数行列であり、分母因子 `M(λ)` は内部になります。結果として得られる行列ペア `(Ani,Eni)` と `(Ami,Emi)` は（一般化された）シュール形式になります。システム `sys` は安定領域 `Cs` の境界上に極を持ってはいけません。固有値の観点から、これは連続時間システムの場合、`A-λE` が虚軸上に制御可能な固有値を持たないこと（単純な無限固有値を除く）を要求し、離散時間システムの場合、`A-λE` が原点を中心とした単位円上に制御可能な固有値を持たないことを要求します。

`Cs` の境界上の極の存在を評価するために、キーワードパラメータ `offset = β` を介して境界オフセット `β` を指定できます。したがって、連続時間システムの場合、`Cs` の境界は実部が区間 `[-β,β]` にある複素数を含み、離散時間システムの場合、`Cs` の境界は絶対値が区間 `[1-β,1+β]` にある複素数を含みます。`β` に使用されるデフォルト値は `sqrt(ϵ)` であり、ここで `ϵ` は作業機械精度です。

`mindeg = false` の場合、両方の因子 `sysni` と `sysmi` は同じ次数の記述子実現を持ち、`Ani = Ami`、`Eni = Emi`、および `Bni = Bmi` となります。`mindeg = true` の場合、`sysmi` の実現は最小です。`sysmi` の（有限）極の数は `sys` の不安定な有限極の数に等しくなります。

`mininf = false` の場合、`Ani-λEni` と `Ami-λEmi` は単純な無限固有値を持つ可能性があります。`mininf = true` の場合、`Ani-λEni` と `Ami-λEmi` は単純な無限固有値を持ちません。単純な無限固有値の除去には行列の逆行列計算が関与することに注意してください。

キーワード引数 `atol1`、`atol2`、`atol3`、および `rtol` はそれぞれ、`A` の非ゼロ要素の絶対許容誤差、`E` の非ゼロ要素の絶対許容誤差、`B` の非ゼロ要素の絶対許容誤差、および `A`、`E`、`B` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `ϵ` は作業機械エプシロンです。キーワード引数 `atol` を使用して、`atol1 = atol`、`atol2 = atol`、`atol3 = atol` を同時に設定できます。

`A-λE` の有限および無限固有値の予備的な分離は、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解に基づくランク決定を使用して行われ、`fast = false` の場合はより信頼性の高いSVD分解が使用されます。

*方法:* [1] の再帰的因子分解アプローチの拡張が使用されます（詳細については [2] を参照）。ペア `(Ani,Eni)` と `(Ami,Emi)` は、両方の `Ani` と `Ami` が準上三角行列であり、`Eni` と `Emi` が両方とも上三角行列または両方ともUniformScalingsである*一般化されたシュール形式*を生成します。

*参考文献:*

[1] A. Varga. Computation of coprime factorizations of rational matrices.     Linear Algebra and Its Applications, vol. 271, pp.88-115, 1998.

[2] A. Varga. On recursive computation of coprime factorizations of rational matrices.      arXiv:1703.07307, https://arxiv.org/abs/1703.07307, 2020. (Linear Algebra and Its Applicationsに掲載予定)
