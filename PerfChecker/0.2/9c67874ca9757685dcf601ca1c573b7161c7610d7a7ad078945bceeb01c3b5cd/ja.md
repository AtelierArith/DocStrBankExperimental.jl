一般的な使用法：

```julia
@check :name_of_backend config_dictionary begin
    # 予備コード
end begin
    # パフォーマンステストを行いたい実際のコード
end
```

`CheckerResult` を出力し、他の関数と一緒に使用できます。  
