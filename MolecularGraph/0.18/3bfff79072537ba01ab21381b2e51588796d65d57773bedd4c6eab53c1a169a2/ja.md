```
inchitosdf(inchi::String; options::String = "") -> Union{String,Nothing}
```

inchi文字列からsdf文字列を生成します。`options`はhttps://github.com/mojaie/libinchi/blob/master/INCHI*BASE/src/inchi*api.hで指定されています。
