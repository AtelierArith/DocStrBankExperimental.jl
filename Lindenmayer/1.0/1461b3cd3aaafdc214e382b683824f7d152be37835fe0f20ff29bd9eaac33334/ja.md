```
drawLSystem(lsystem::LSystem ;
       # オプション設定:
       forward=15,
       turn=45,
       iterations=10,
       filename="lsystem.png",
       width=800,
       height=800,
       startingpen=(0.3, 0.6, 0.8), # 開始色 RGB
       startingx=0,
       startingy=0,
       startingorientation=0,
       showpreview=true,
       backgroundcolor = colorant"black",
       asteriskfunction = (t::Luxor.Turtle) -> ())
```

リンダマイヤーシステムを描画します。 `lsystem` はL-Systemの定義（初期状態に従ったルール）です。

例えば:

```
newsystem = LSystem(Dict("F" => "AGCFCGAT", "G" => "CFAGAFC"), "F")
```

次のようにルールを変更または追加できます:

```
newsystem.rules["F"] = "OFO"
```

タートルコマンド "1" ... "9" を使用して適切な線の太さ（ポイント単位）を選択するか、"n" を選択して狭い0.5を選ぶことで、線の太さを変えることができます。
