```
@fileval <path> <global opts> <substitutions (singleton range)>
```

ファイル内のパラメータ化された式の内包を展開し評価し、結果の式を評価します。`mode=string`を使用して、入力を文字列として処理します（その後、解析され評価されます）。

# 例

```
@fileval "file.jl" mode=expr x=1 # "file.jl"の内容を式として扱う（最初に解析し、その後展開）
@fileval file_string.jl mode=string x=1 # 最初に文字列として展開し、その後 
```
