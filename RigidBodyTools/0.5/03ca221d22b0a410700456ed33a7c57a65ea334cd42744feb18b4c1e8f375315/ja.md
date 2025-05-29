```
ExogenousDOF() <: AbstractDOFKinematics
```

DOFを制約付きとして設定しますが、その動作は毎瞬間に外因的プロセスによって設定されます。このようなDOFには、ベクトル `[x,ẋ,ẍ]` を提供する必要があります。
