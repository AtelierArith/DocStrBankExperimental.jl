```julia
sync_get_depth_with_res(
    depth,
    timestamp,
    index,
    res,
    fmt
) -> Int32

```

同期深度関数、実行ループが実行されていない場合は開始します

生ポインタバージョンでは、返されたバッファはこの関数が再度呼び出されるまで有効であり、その後はバッファを再度使用してはいけません。データが必要な場合はコピーを作成してください。配列を返すバージョンにはこの制限はありません。
