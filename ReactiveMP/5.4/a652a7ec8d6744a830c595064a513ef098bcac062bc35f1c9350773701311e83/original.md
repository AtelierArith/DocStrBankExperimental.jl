The PlanarFlow function is defined as

$$
f({\bf{x}}) = {\bf{x}} + {\bf{u}} \tanh({\bf{w}}^\top {\bf{x}} + b)
$$

with input and output dimension $D$. Here ${\bf{x}}\in \mathbb{R}^D$ represents the input of the function. Furthermore ${\bf{u}}\in \mathbb{R}^D$, ${\bf{w}}\in \mathbb{R}^D$ and $b\in\mathbb{R}$ represent the parameters of the function. The function contracts and expands the input space. 

This function has been introduced in:

Rezende, Danilo, and Shakir Mohamed. "Variational inference with normalizing flows." *International conference on machine learning.* PMLR, 2015.
