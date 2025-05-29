```
eop_generate_from_txt(m::IERSModel, inputfile, outputfile)
```

IERS EOP データを含む TXT ファイルを解析し、関連情報を専用の JSMD `.eop.dat` ファイルに抽出します。サポートされているフォーマットは EOP C04 シリーズと Rapid Data 予測（最終版）です。

!!! note
    `outputfile` の名前にはファイル拡張子を含めないでください。この関数によって自動的に追加されます。


!!! note
    ファイルの種類に応じて、CIP または摂動補正が存在する場合があります。この関数は、欠落しているデータを自動的に取得するための変換アルゴリズムを適用します。


!!! warning
    このルーチンは、入力ファイル名を分析することによってファイル構造と列の順序を認識します。この名前は IERS ウェブサイトから取得したものと同じにしておく必要があります。


### References

  * [USNO finals](https://maia.usno.navy.mil/ser7/readme.finals)
  * [USNO finals 2000A](https://maia.usno.navy.mil/ser7/readme.finals2000A)

### See also

See also [`eop_generate_from_csv`](@ref). 
