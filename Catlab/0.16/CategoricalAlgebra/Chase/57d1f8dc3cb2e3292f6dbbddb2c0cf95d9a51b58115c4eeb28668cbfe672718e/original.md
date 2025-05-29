The chase is an algorithm which subjects a C-Set instance to constraints  expressed in the language of regular logic, called embedded dependencies  (EDs, or 'triggers'). 

A morphism S->T, encodes an embedded dependency. If the pattern  S is matched (via a homomorphism S->I), we demand there exist a morphism T->I  (for some database instance I) that makes the triangle commute in order to  satisfy the dependency (if this is not the case, then the trigger is 'active').

Homomorphisms can merge elements and introduce new ones. The former kind are called "equality generating dependencies" (EGDs) and the latter "tuple generating dependencies" (TGDs). Any homomorphism can be factored into EGD and TGD components by, respectively, restricting the codomain to the image or restricting the domain to the coimage.
