import numpy as np

import scipy as sc

import pandas as pd

from fractions import Fraction

def float_format(vector, decimal):

    return np.round((vector).astype(np.float), decimals=decimal)
    
dp = Fraction(1,3)

M = np.matrix([[0,0,1],
        [Fraction(1,2),0,0],
        [Fraction(1,2),1,0]])

E= np.zeros((3,3))

E[:] = dp

d = 0.8

A = d * M + ((1-d) * E)

r = np.matrix([dp, dp, dp])

r = np.transpose(r)

previous_r = r

for it in range(1,100):

    r = A * r
    
    print(float_format(r,3))
    
    if (previous_r==r).all():
    
        break
        
    previous_r = r
    
print ("Final:\n", float_format(r,3))

print ("sum", np.sum(r))
