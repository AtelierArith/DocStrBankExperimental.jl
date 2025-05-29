```
xkb_utf32_to_keysym(ucs)
```

Unicode/UTF-32 コードポイントに対応するキースymを取得します。

この関数は xkb*keysym*to_utf32 の逆です。単一のコードポイントが複数のキースymに対応する場合、最も低い値のキースymを返します。

特別な（レガシー）キースym エンコーディングを持たない Unicode コードポイントは、直接エンコーディング方式を使用します。これらのキースymには通常、関連するキースym 定数 (XKB*KEY**) はありません。

非文字の Unicode コードポイントおよび定義された Unicode プレーンの外にあるコードポイントに対して、この関数は [`XKB_KEY_NoSymbol`](@ref) を返します。

\since 1.0.0

### 戻り値

指定された Unicode コードポイントに対応するキースym、または存在しない場合は [`XKB_KEY_NoSymbol`](@ref) を返します。

### 参照

[`xkb_keysym_to_utf32`](@ref)()
