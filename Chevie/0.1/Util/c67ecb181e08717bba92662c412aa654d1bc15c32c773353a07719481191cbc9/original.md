`@forward T.f f1,f2,...`

is a macro which delegates definitions. The above generates 

```
f1(a::T,args...)=f1(a.f,args...)
f2(a::T,args...)=f2(a.f,args...)
...
```
