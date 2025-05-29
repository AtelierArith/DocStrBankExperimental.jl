```
random_flow_field(;component=:Rotational,np=12,nq=18,format=:Array)
```

Generate random flow fields on a grid of `np x nq` points for use in simple examples.

The `:Rotational` component option is most similar to what is done  in the standard example.

The `:Divergent` component option generates a purely divergent flow field instead.

```
(U,V,Φ)=random_flow_field(component=:Rotational)
F=convert_to_FlowFields(U,V,10.0)
I=Individuals(F,x,y,fill(1,length(x)))
```
