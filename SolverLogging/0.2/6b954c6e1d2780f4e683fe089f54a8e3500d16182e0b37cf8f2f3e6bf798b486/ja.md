```
@log [logger] args...
```

`logger`を使用してデータをログします。指定されていない場合はデフォルトのロガーが使用されます。以下のいずれかの形式であることができます：

```
@log "name" 1.0    # リテラル値
@log "name" 2a     # 式
@log "name" name   # 変数
@log name          # 前のショートカット
```

指定されたエントリが現在の冗長性レベルでアクティブである場合、
