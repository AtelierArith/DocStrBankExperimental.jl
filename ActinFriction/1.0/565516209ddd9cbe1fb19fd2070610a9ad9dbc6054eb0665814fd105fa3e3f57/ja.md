```julia
savename(
    prefix,
    params;
    digits,
    suffix,
    ignored_fields
) -> Union{Base.AnnotatedString{String}, String}

```

パラメータのセットからファイル名を生成します。

これは、丸めと末尾のゼロの処理が改善されたDrWatson関数の代替です。
