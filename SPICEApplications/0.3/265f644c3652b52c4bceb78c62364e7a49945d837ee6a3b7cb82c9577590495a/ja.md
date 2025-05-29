```julia
msopck(
;
    setup,
    input,
    output,
    stdout,
    stderr,
    stdin,
    append,
    wait
)

```

MSOPCKは、UTC、SCLK、またはETタグ付きの四元数、オイラー角、または行列としてテキストファイルに提供された姿勢データを、オプションで角速度を伴いながら、タイプ1、2、または3のSPICE Cカーネルに変換するコマンドラインプログラムです。
