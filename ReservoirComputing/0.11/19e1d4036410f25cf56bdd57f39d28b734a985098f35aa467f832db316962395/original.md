```
StandardRidge([Type], [reg])
```

Returns a training method for `train` based on ridge regression. The equations for ridge regression are as follows:

$$
\mathbf{w} = (\mathbf{X}^\top \mathbf{X} + 
\lambda \mathbf{I})^{-1} \mathbf{X}^\top \mathbf{y}
$$

# Arguments

  * `Type`: type of the regularization argument. Default is inferred internally, there's usually no need to tweak this
  * `reg`: regularization coefficient. Default is set to 0.0 (linear regression).

```
