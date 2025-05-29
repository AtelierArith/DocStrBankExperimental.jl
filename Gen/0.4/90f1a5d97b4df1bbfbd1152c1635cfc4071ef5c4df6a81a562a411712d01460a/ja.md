```
value = get_value(choices::ChoiceMap, addr)
```

指定されたアドレスの値を返すか、値が存在しない場合はKeyErrorをスローします。構文糖は`Base.getindex`です：

```
value = choices[addr]
```
