```
eop_generate_from_csv(m::IERSModel, inputfile, outputfile)
```

IERS EOPデータを含むCSVファイルを解析し、関連情報を専用のJSMD `.eop.dat`ファイルに抽出します。サポートされているフォーマットはEOP C04シリーズとRapid Data予測（finals）です。

!!! note
    `outputfile`の名前にはファイル拡張子を含めないでください。この関数によって自動的に追加されます。


!!! note
    ファイルの種類に応じて、CIPまたは歳差補正が存在する場合があります。この関数は、欠落データを自動的に取得するための変換アルゴリズムを適用します。


!!! warning
    Rapid Data予測ファイルは、LOD、CIP、および歳差補正をそれぞれミリ秒およびミリ秒角で保存しますが、EOP C04ファイルはそうではありません。このルーチンは、入力ファイル名のフォーマットを分析することによって、正しい単位を自動的に検出します。したがって、ファイル名はIERSによってリリースされたものと同じに保つ必要があります。


### References

  * [USNO finals](https://maia.usno.navy.mil/ser7/readme.finals)
  * [USNO finals 2000A](https://maia.usno.navy.mil/ser7/readme.finals2000A)

### See also

[`eop_generate_from_txt`](@ref)も参照してください。
