```
textplace(txt::T where T <: AbstractString, pos::Point, params::Vector;
    action = :fill,
    startnewpath = false)
```

パラメータ `params` に従って、テキスト文字を1つずつ配置する低レベルの関数です。最初の文字は最初のタプルを使用し、2番目の文字は2番目を使用し、以下同様です。

次のテキスト位置を返します。

パラメータのタプルは次のようになります：

```julia
(face = "TimesRoman", size = 12, color=colorant"black", kern = 0, shift = 0, advance = true)
```

ここで

  * `face` はフォントフェイス "string"                   # スティッキー
  * `size` はフォントサイズ # pts                      # スティッキー
  * `color` は色                                      # スティッキー
  * `kern` は右にシフトされた量 (ピクセル)           # 各文字の後にリセット
  * `shift` = ベースラインが垂直にシフトされる       # 各文字の後にリセット
  * `advance` - 進むかどうか                          # 各文字の後にリセット

一部のパラメータは「スティッキー」であり、一度設定されると新しい値が供給されるまで全ての後続の文字に適用されます。他のパラメータはスティッキーではなく、各文字ごとにリセットされます。したがって、フォントフェイス、サイズ、および色のパラメータは一度だけ指定すればよく、kern/shift/advance 修飾子は各文字ごとにリセットされます。

## 例

ホグワーツ特急プラットフォーム番号 9 と 3/4 を描画します：

```julia
txtpos = textplace("93—4!", O - (200, 0), [
    # 9 のフォーマット:
    (size=120, face="Bodoni-Poster", color=colorant"grey10"),
    # 3 のフォーマット:
    (size=60,  kern = 5, shift = 60,  advance=false,),
    # - のフォーマット:
    (          kern = 0, shift = 25,  advance=false,),
    # 4 のフォーマット:
    (          kern = 5, shift = -20, advance=true),
    # ! のフォーマット:
    (size=120, kern = 20,),
    ])
```
