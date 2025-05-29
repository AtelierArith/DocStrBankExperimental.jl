```
@check vkCreateInstance(args...)
```

式を `_return_code` という変数に代入します。次に、値が成功コードでない場合は、戻りコードを保持する [`VulkanError`](@ref) を返します。
