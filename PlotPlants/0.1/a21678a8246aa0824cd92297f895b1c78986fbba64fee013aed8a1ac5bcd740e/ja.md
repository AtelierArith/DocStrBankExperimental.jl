```
set_titles!(axs::Array;
            labels::Array{String,1} = String[],
            paren::Bool = true,
            capital::Bool = false,
            dotsep::Bool = false,
            fontsize::Number = 16,
            loc::String = "center",
            usetex::Bool = true
)
```

軸のタイトルを設定します。与えられたものは

  * `axs` 軸の配列
  * `labels` オプション: パネルタイトルの後のラベル、例: `(a) label`
  * `paren` オプション: trueの場合、`(a)`のような形式を使用
  * `capital` オプション: trueの場合、大文字を使用、例: `(A)`
  * `dotsep` オプション: trueの場合、ラベルの後にドットを追加、例: `(a).`
  * `fontsize` オプション: タイトルのフォントサイズ
  * `loc` オプション: タイトルの位置
  * `usetex` オプション: latexレンダリングを使用
