```
write_script(script_file::AbstractString,gp::GnuplotScript)
```

将来使用のために埋め込まれたデータを持つスクリプトを書きます。

# 使用法

```julia
gp = GnuplotScript()

...

write_script("gnuplot_script.gp",gp)
```

Gnuplotを使用してスクリプトを再生できます：

```sh
    gnuplot gnuplot_script.gp
```

gnuplotセッションを開いたままにしたい場合は、最後に `-` を追加します。

```sh
    gnuplot gnuplot_script.gp -
```
