```
Weingarten(M, p, X, V)
```

Compute the Weingarten map $\mathcal W_p\colon T_p\mathcal M × N_p\mathcal M \to T_p\mathcal M$, where $N_p\mathcal M$ is the orthogonal complement of the tangent space $T_p\mathcal M$ of the embedded submanifold $\mathcal M$, where we denote the embedding by $\mathcal E$.

The Weingarten map can be defined by restricting the differential of the orthogonal [`project`](@ref)ion $\operatorname{proj}_{T_p\mathcal M}\colon T_p \mathcal E \to T_p\mathcal M$ with respect to the base point $p$, i.e. defining

$$
\mathcal P_X := D_p\operatorname{proj}_{T_p\mathcal M}(Y)[X],
\qquad Y \in T_p \mathcal E, X \in T_p\mathcal M,
$$

the Weingarten map can be written as $\mathcal W_p(X,V) = \mathcal P_X(V)$.

The Weingarten map is named after [Julius Weingarten](https://en.wikipedia.org/wiki/Julius_Weingarten) (1836–1910).
