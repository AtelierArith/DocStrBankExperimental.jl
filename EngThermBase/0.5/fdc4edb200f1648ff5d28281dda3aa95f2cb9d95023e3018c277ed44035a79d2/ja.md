`molParse(txt::AbstractString)::Molecule`

`txt`引数を解析します—"CH4"や"(CH3)2(CH2)6"のようなもの—対応する`Molecule`オブジェクトを返します。`txt`に無効な文字が含まれている場合や、すべての括弧が閉じられていない場合は処理を中止します。
