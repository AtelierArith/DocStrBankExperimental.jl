```
wait_for_visible(element::ElementHandle; retry_delay::Real = 0.3,
    timeout::Real = 10, visible::Bool = true)
```

要素が表示されるのを待ちます。ただし、`visible` が false の場合（＝「非表示」要素）を除きます。タイムアウトに達した場合は TimeoutError をスローします。
