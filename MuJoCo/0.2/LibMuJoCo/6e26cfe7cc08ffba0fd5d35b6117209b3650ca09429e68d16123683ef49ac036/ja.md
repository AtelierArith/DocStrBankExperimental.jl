```
mju_boxQPmalloc(res, R, index, H, g, n, lower, upper)
```

ボックス制約付き二次計画のためにヒープメモリを割り当てます。mju*boxQPのように、index、lower、およびupperはオプションです。すべてのポインタはmju*free()で解放してください。
