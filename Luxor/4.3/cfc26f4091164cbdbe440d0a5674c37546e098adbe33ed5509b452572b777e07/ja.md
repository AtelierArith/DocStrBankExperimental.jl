```
label(txt::T where T <: AbstractString, alignment::Symbol=:N, pos::Point=O;
    offset=5,
    leader=false,
    leaderoffsets=[0.0, 1.0])
```

ポイントにテキストラベルを追加し、そのポイントに対して相対的に配置します。たとえば、`:N`は北を示し、テキストをそのポイントの真上に配置します。

`:N`、`:S`、`:E`、`:W`、`:NE`、`:SE`、`:SW`、`:NW`のいずれかを使用して、ラベルをそのポイントに対して相対的に配置します。

```julia
label("text")          # 原点に対して北（上）にテキストを配置します
label("text", :S)      # 原点に対して南（下）にテキストを配置します
label("text", :S, pt)  # ptの南にテキストを配置します
label("text", :N, pt, offset=20)  # ptの北にテキストを配置し、オフセットを20にします
```

デフォルトのオフセットは5単位です。

`leader`がtrueの場合、線も描画します。

`leaderoffsts`は、指定されたポイントと線の開始および終了の間のギャップを指定するために正規化された分数を使用します（`between()`を参照）。

TODO: 負のオフセットは良い結果をもたらしません。
