```
F"some string"
```

`FortranString{Char}("some string")`の文字列マクロです。

`'d'`および`"qq"`フラグは、ダブルクオート内の文字列のFortran文字列の動作をエミュレートするために使用できます。このような文字列内のダブルクオートは二重にする必要があります：

```
F8"Use \"\"doubled\"\""qq
```

`'q'`フラグは、シングルクオート内のFortran文字列のエミュレーションを示します：

```
F8"Can''t be with only single quote inside"q
```
