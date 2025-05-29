```
NetworkArg(model, protocol,params,paralinks,tissuetype,sigma,noise_type,dropoutp=0.2)
```

Use the inputs related to biophysical models to determine network architecture and number of training samples for test return a full defined NetworkArg struct 

Reference for adjusting the number of training samples: Shwartz-Ziv, R., Goldblum, M., Bansal, A., Bruss, C.B., LeCun, Y., & Wilson, A.G. (2024). Just How Flexible are Neural Networks in Practice?

(Easier task and smaller MLPs have higher effective model complexity (can fit more training samples than network parameters;  for more complex tasks and larger MLPs, the number of training samples can be set as similar to the number of network parameters to improve training efficiency)
