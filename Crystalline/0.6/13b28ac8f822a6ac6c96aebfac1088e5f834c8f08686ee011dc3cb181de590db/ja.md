```julia
mulliken(pgir::Crystalline.PGIrrep{D}) -> String

```

ポイントグループの不変量 `pgir` のマリケンラベルを返します。

## 注意事項

この機能は、ビルバオ結晶学データベース [^2] のリストを使用して、表にまとめられたCDMLポイントグループ不変量ラベルと関連するマリケンラベルとの間の単純なマッピングです [^1]。

下付き文字を無視すると、マリケンラベルの割り当てに関連する大まかなルールは次のとおりです。

1. **不変量の次元性**: 

      * **1次元不変量**: 実不変量の場合、AまたはBを割り当てます（主回転に対して反対称の場合はB）。複素不変量の場合、ラベル¹Eまたは²Eを割り当てます。
      * **2次元不変量**: ラベルEを割り当てます。
      * **3次元不変量**: ラベルTを割り当てます。
2. ***u*および*g*の下付き文字**: グループに反転が含まれている場合、不変量が反転に対して対称（g ~ gerade）か反対称（u ~ ungerade）であるかを示します。
3. **プライム上付き文字**: グループに主回転軸に沿った鏡*m*が含まれているが、反転が含まれていない場合、この鏡に対して不変量が対称（′）か反対称（′′）であるかを示します。
4. **数字の下付き文字**: 数字の下付き文字の割り当てに関するルールは一般的に非常に複雑であり、実際には一般的な一貫したルールを知らないため、ここでは説明できません。

## 参考文献

[^1]: Mulliken, Report on Notation for the Spectra of Polyatomic Molecules,    [J. Chem. Phys. *23*, 1997 (1955)](https://doi.org/10.1063/1.1740655).

[^2]: Bilbao Crystallographic Database's   [Representations PG program](https://www.cryst.ehu.es/cgi-bin/cryst/programs/representations_point.pl?tipogrupo=spg).
