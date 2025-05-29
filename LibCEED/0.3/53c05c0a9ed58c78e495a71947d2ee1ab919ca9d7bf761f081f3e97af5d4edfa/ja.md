```
CeedVector(c::Ceed, len::Integer; allocate::Bool=true)
```

指定された長さの`CeedVector`を作成します。`allocate`がfalseの場合、メモリは割り当てられません。`setarray!`を呼び出す前にベクターにアクセスしようとすると失敗します。デフォルトでは、`allocate`はtrueであり、libCEEDはベクターのために（ホスト）メモリを割り当てます。
