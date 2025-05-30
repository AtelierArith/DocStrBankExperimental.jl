```
State(func)

State() do state
  ....
  return value, newstate
end
```

状態モナドは、状態をモナディック型内にカプセル化し、状態管理のモナディックカプセル化を提供します。

状態は、呼び出すか、`Base.run`を使用することで実行できます。初期状態が指定されていない場合、`nothing`が使用されます。
