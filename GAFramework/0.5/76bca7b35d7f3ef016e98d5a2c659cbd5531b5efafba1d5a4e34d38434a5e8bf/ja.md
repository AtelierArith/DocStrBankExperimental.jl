```
crossover!(z, x,y, model::GAModel, aux, rng)
```

xとyを交差させて子を作成します。オプションで、zのスペースをスクラッチスペースとして使用するか、子を作成するために使用します。auxはさらにスクラッチスペースです。rngは乱数生成器です。     model = GAM(G1,G2)     aux = genauxga(model)     x = randcreature(model,aux)     y = randcreature(model,aux)     z = randcreature(model,aux)     child = crossover(z,x,y,model,aux,rng)
