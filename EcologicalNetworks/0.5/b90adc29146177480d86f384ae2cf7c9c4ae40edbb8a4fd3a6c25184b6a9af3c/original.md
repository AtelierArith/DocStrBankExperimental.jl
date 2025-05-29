```
connectance(N::AbstractEcologicalNetwork)
```

Number of links divided by the number of possible interactions. In unipartite networks, this is $L/S^2$. In bipartite networks, this is $L/(T × B)$. It is worth noting that while the maximal connectance is always 1 (i.e. the graph is complete), the minimum value (assuming that the network is not degenerate) is *not* 0. Instead, the minimum number of interactions in a unipartite network is `S-1`, and in a bipartite network it is `max(T,B)`.

Connectance can therefore be transformed between 0 and 1, using the following approach: let `m` be the minimum number of interactions, and Co be the measured connectance, then the corrected value is `(Co-m)/(1-m)`. To our best knowledge, this is not standard practice, and therefore is not suggested as a function in the package.

#### References

  * Delmas, E., Besson, M., Brice, M.-H., Burkle, L.A., Dalla Riva, G.V., Fortin, M.-J., Gravel, D., Guimarães, P.R., Hembry, D.H., Newman, E.A., Olesen, J.M., Pires, M.M., Yeakel, J.D., Poisot, T., 2018. Analysing ecological networks of species interactions. Biological Reviews 112540. https://doi.org/10.1111/brv.12433
  * Dunne, J.A., 2006. The Network Structure of Food Webs, in: Dunne, J.A., Pascual, M. (Eds.), Ecological Networks: Linking Structure and Dynamics. Oxford University Press, pp. 27–86.
  * Martinez, N.D., 1992. Constant Connectance in Community Food Webs. The American Naturalist 139, 1208–1218.
