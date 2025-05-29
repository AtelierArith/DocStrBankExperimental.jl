```
import_technologies(techFile::String, case_file::String;
                    sourceGroup::String="U", sourceAddGroup::String="Uadd",
                    sinkGroup::String="D")
```

技術を定義する `json` ファイルとケースを定義するファイルをインポートします。後者は適合性スコアを計算するために使用されます。

i) ソースの配列、ii) 追加ソースの配列、iii) TAS スコアを持つすべての技術の配列を返します。
