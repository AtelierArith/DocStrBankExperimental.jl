与えられた各変数の値に対して、置換を適用する射 X → X′ を作成します。これをプッシュアウトを介して行います。

O –> X    ここで C は `merge` 同値類の AttrVars を持ち    ↓          そして O は AttrVars のみを持ち（具体的な値または同値類に送られる）    C          C への写像において。

`subs` と `merge` は attrtype 名でキー付けされた辞書です。

`subs` の値はバインディングを示す整数キー付き辞書で、例えば `; subs = (Weight = Dict(1 => 3.20, 5 => 2.32), ...)` のようになります。

`merge` の値は同値類を示すベクトルのベクトルで、例えば `; merge = (Weight = [[2,3], [4,6]], ...)` のようになります。
