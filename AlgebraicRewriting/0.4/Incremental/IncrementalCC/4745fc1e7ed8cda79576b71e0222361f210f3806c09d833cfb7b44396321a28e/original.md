Delete / modify existing matches based on the target ACSet being permuted or  reduced to a subobject. If a match touches upon something which is deleted,  remove the match. Given X ↩ X′ we are updating Hom(L, X) => Hom(L, X′)

In the presence of negative application conditions / dangling condition,  a deletion can also *add* new matches. When deletion is performed by DPO, we  can know statically where to search for newly added morphisms. However, if we  simply have an arbitrary deletion, this is harder. 

A NAC has been deactivated if there exists a morphism N ⇾ X that sends  all of L to the nondeleted part of X & *some* of N to the deleted portion. The  deleted portion should be *tiny* compared to the not deleted portion, so it's  pretty bad to search for all morphisms N->X and filter by those which have  something which has something in the deleted portion. This means we ought to  compute the overlaps on the fly in the non-DPO case. 

The `dpo` flag signals that `f` was produced via pushout complement, such that  any NAC can take advantage of its cached overlaps if it has them. If it is not  nothing, it contains the morphism `L ↢ I` that was used in POC.

Returns the 'keys' of the deleted matches and added matches.
