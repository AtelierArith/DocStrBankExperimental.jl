```
F8"some string"
```

FORTRAN文字列と互換性のある文字列マクロ `FortranString{UInt8}`。

`'d'` および `"qq"` フラグは、ダブルクオート内の文字列でFORTRAN文字列の動作をエミュレートするために使用できます。このような文字列内のダブルクオートは二重にする必要があります：

```
F8"Use \"\"doubled\"\""qq
```

`'q'` フラグは、シングルクオート内のFORTRAN文字列のエミュレーションを示します：

```
F8"Can''t be with only single quote inside"q
```
