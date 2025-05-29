```
scatter(cmd0::String="", arg1=nothing; kwargs...)
```

(x,y) ペアを読み取り、それらの位置に地図上にシンボルをプロットします。このモジュールは、散布図を描くために簡素化された $plot$ のサブセットです。そのため、多くの（細かい）制御パラメータはここには記載されていません。より細かい制御が必要な場合は、$plot$ モジュールを参照してください。

## パラメータ

  * **G** | **fill** | **markerfacecolor** :: [Type => Str]

    シンボルやポリゴンの塗りつぶしの色またはパターンを選択します。
  * **N** | **noclip** | **no_clip** :: [Type => Str | []]

    地図の境界の外にあるシンボルをクリップしない
  * **P** | **portrait** :: [Type => Bool or []]

    GMT に **NOT** 縦向きモードで描画するように指示します（つまり、横向きのプロットを作成します）
  * **S** :: [Type => Str]

    シンボルをプロットします（ベクトル、パイのスライス、前線、装飾されたまたは引用された線を含む）。

    または、エイリアスを使用してシンボルのサブセットを選択します: **symbol** または **marker** と値:

      * **-**, **x_dash**
      * **+**, **plus**
      * **a**, *, **star**
      * **c**, **circle**
      * **d**, **diamond**
      * **g**, **octagon**
      * **h**, **hexagon**
      * **i**, **v**, **inverted_tri**
      * **n**, **pentagon**
      * **p**, **.**, **point**
      * **r**, **rectangle**
      * **s**, **square**
      * **t**, **^**, **triangle**
      * **x**, **cross**
      * **y**, **y_dash**

```
および **markersize** または **size** キーワードでサイズを選択します [デフォルトは 8p です]。
マーカーサイズはスカラーまたはデータの行数と同じサイズのベクトルにすることができます。単位は
特に指定されていない限りポイントです（例えば cm の場合） *par=(PROJ_LENGTH_UNIT=:c,)*
```

  * **W** | **pen** | **markeredgecolor** | **mec** :: [Type => Str]

    線またはシンボルのアウトラインのペン属性を設定します
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext` で図を保存します。ここで `ext` は図のフォーマットを選択します（例: figname="name.png"）

[`GMT man page`](http://docs.generic-mapping-tools.org/latest/plot.html)
