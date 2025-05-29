The Apogee to Apogee Path Sampler (AAPS) by Sherlock et al. (2022). 

AAPS is a simple alternative to the No U-Turn Sampler (NUTS). It serves a similar purpose as NUTS: the method should be robust to its choice  of tuning parameters when compared to standard HMC. For a given starting position and momentum (x, v), AAPS explores both forward and  backward trajectories. The trajectories are divided into segments, with  segments being separated by apogees (local maxima) in the energy landscape  of -log pi(x). The tuning parameter `K` defines the number of segments to explore. 
