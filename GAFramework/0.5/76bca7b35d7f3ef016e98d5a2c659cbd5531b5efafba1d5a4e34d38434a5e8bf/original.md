```
crossover!(z, x,y, model::GAModel, aux, rng)
```

Crosses over x and y to create a child. Optionally use space in z as a scratch space or to create the child. aux is more scratch space. rng is random number generator.     model = GAM(G1,G2)     aux = genauxga(model)     x = randcreature(model,aux)     y = randcreature(model,aux)     z = randcreature(model,aux)     child = crossover(z,x,y,model,aux,rng)
