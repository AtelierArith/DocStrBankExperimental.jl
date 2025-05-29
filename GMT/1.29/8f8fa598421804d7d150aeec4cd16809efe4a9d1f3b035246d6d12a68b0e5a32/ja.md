```
stackgrids(names::Vector{String}, v=nothing; zcoord=nothing, zdim_name="time",
           z_unit="", save="", mirone=false)
```

単一のグリッドをマルチバンドキューブのようなファイルにスタックします。

  * `names`: スタックするグリッドの名前を含む文字列ベクター
  * `v`: 垂直座標を含むベクター。提供されない場合は、1:length(names)のものが生成されます。

      * `v`がTimeTypeの場合、`z_unit`キーワードを使用してファイルに保存する内容を選択します（大文字と小文字は区別されません）。

          * `decimalyear`または`yeardecimal`はDateTimeを小数年（Float64）に変換します
          * `milliseconds`（または単に`mil`）はDateTimeを0000-01-01T00:00:00からのミリ秒として保存します（Float64）
          * `seconds`はDateTimeを0000-01-01T00:00:00からの秒として保存します（Float64）
          * `unix`はDateTimeを1970-01-01T00:00:00からの秒として保存します（Float64）
          * `rata`はDateTimeを0000-12-31T00:00:00からの日数として保存します（Float64）
          * `Date`または`DateTime`はDateTimeの文字列表現として保存します。
  * `zdim_name`: 垂直軸の名前（デフォルトは"time"）
  * `zcoord`: `v`と同じキーワード（どちらか一方を使用できます）。
  * `save`: 作成されるファイルの名前。
  * `mirone`: キューブファイルを作成せず、代わりに"automatic_list.txt"（または`save=xxx`の任意の名前）というファイルを作成し、Mironeの`Empilhador`ツールで使用します。
