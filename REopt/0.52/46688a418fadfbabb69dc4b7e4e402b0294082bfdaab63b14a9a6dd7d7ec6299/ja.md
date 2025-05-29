```
REoptInputs(fp::String)
```

`fp`を使用してJSONシナリオをロードします：

```
function REoptInputs(fp::String)
    s = Scenario(JSON.parsefile(fp))
    REoptInputs(s)
end
```

モデルを解く前にREoptInputsを手動で修正したい場合に便利です。
