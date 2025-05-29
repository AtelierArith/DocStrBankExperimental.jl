```
ParallelProcessingTools.original_exception(err)
```

`TaskFailedException`や`RemoteException`のような（ネストされた可能性のある）例外を、元々スローされた可能性が高い最も内側の例外に置き換えます。他の例外は変更されません。
