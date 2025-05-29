```
@userfriendly_exceptions expr
```

`expr` から発生する例外を、よりユーザーフレンドリーなものに変換します。

`expr` の並列コードから複数の例外が発生した場合、再スローされるのは1つだけで、`TaskFailedException` と `RemoteException` は、それらを引き起こした元の例外に置き換えられます。

[`inner_exception`] と [`onlyfirst_exception`](@ref) を参照してください。
