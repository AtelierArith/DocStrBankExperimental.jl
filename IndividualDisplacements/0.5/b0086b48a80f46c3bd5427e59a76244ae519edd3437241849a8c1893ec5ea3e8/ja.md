```
random_flow_field(;component=:Rotational,np=12,nq=18,format=:Array)
```

グリッドの `np x nq` ポイントでランダムフローフィールドを生成し、シンプルな例で使用します。

`:Rotational` コンポーネントオプションは、標準的な例で行われるものに最も似ています。

`:Divergent` コンポーネントオプションは、純粋に発散するフローフィールドを生成します。

```
(U,V,Φ)=random_flow_field(component=:Rotational)
F=convert_to_FlowFields(U,V,10.0)
I=Individuals(F,x,y,fill(1,length(x)))
```
