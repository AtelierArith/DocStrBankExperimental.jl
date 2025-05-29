Get list of possible matches based on the constraints of the rule

This function has the same behavior as the generic `get_matches`, but it is  more performant because we do not have to query all homomorphisms before finding  a valid match, in case n=1. 
