A ProjMPOSum computes and stores the projection of an implied sum of MPOs into a basis defined by an MPS, leaving a certain number of site indices of each MPO unprojected. Which sites are unprojected can be shifted by calling the `position!` method. The MPOs used as input to a ProjMPOSum are *not* added together beforehand; instead when the `product` method of a ProjMPOSum is invoked, each projected MPO in the set of MPOs is multiplied by the input tensor one-by-one in an efficient way.

Drawing of the network represented by a ProjMPOSum `P([H1,H2,...])`, showing the case of `nsite(P)==2` and `position!(P,psi,4)` for an MPS `psi` (note the sum Σⱼ on the left):

```
     o--o--o-      -o--o--o--o--o--o <psi|
     |  |  |  |  |  |  |  |  |  |  |
 Σⱼ  o--o--o--o--o--o--o--o--o--o--o Hⱼ
     |  |  |  |  |  |  |  |  |  |  |
     o--o--o-      -o--o--o--o--o--o |psi>
```
