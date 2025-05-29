```
load_particle_data(video_name::AbstractString)
```

`/particle_data`にある粒子データの`.csv`を`DataFrame`に読み込みます。

`.csv`ファイルがImageJからのものである場合（X、Y、Label列を含み、x、y、frameではない）、次の処理を行います：

1. ラベル列からフレーム番号を抽出し、[`extract_frame_from_label`](@ref)を使用して新しい列として追加します。
2. `X`および`Y`列の名前を`x`および`y`に変更し、[`link`](@ref)と連携できるようにします。
3. 名前が空の列を削除します。
4. `Circ.`列の名前を`Circ`に変更し、Juliaのシンボル表記と連携できるようにします。
