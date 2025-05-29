`decompose(ct::CharTable,c::Vector;exact=true)`

`CharTable` `ct` によって与えられた不可約表現に対する共役類の値によって与えられる `c` のクラス関数 `decompose`。デフォルトでは、`c` は仮想表現であると期待されるため、結果は整数ベクトルになります。`c` が仮想表現でない場合は、正しい結果を得るためにキーワード `exact=false` を指定してください。
