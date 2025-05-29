A simple mer count struct.

MerCount is a simple struct that binds a mer value to a count of the number of times it has been observed.

This type, (sorted) vectors of them, and some additional utility methods, can form the basic building blocks of the higher-level mer counting functionality. This struct can also be an eltype of kmer hashes or more involved specialized types that store counts of Kmers.

!!! note
    The count is stored as an UInt8 because often once the count is more than 255 we hardly care anymore.

