import array as arr
import pandas as pd
import math
from scipy.interpolate import make_interp_spline
import numpy as np
import matplotlib.pyplot as plt


#### All the masses in Atomic mass unit (amu or u).
M_p=1.007272
M_X=float(input("Give the amu of the target particle\n"))
M_Y=float(input("Give the amu of the product nucleus\n"))
M_n=1.008664
C=931.494013        #This is the conversion factor between amu(u) and MeV.
c=3*10**8

Q=(M_p+M_X-(M_Y+M_n))*C
print(Q)

E_lab=-1*Q*(1+M_p/M_X)   #E_lab is the threshold energy in the lab frame.
print(E_lab)

E_cm=(M_X/(M_p+M_X))*E_lab    #E_cm is thershold energy in the cm frame.
print(E_cm)

#Where E_c is the coulomb barrier.
A_1=1
A_2=int(input("Give the mass number of Y\n"))
a=(A_1)**(1/3)
b=(A_2)**(1/3)
Z_1=1
Z_2=int(input("Give the charge of Y\n"))
E_c=(1.44/1.3)*((Z_1*Z_2)/(a+b))
print(E_c)


#Where mu is the reduced mass.
mu=(M_p*M_X)/(M_p+M_X)
print(mu)


E=M_X/(M_p+M_X)     #Where E is E_cm/E_lab
print(E)

eta=0.1575*(Z_1)*(Z_2)*(math.sqrt(mu/E_cm))    #Where eta is the sommerfeld parameter.
Gf=2*math.pi*eta       #Where G(E) is the gamow factor.
E_g=0.979*mu*(Z_1*Z_2)**2    #Where E_g is the gamow energy.
print(eta)
print(Gf)
print(E_g)


E_lab=float(input("Input your value\n"))
E_cm=0.9781*E_lab
cs=float(input("Input your value\n"))
a=math.exp(20.63/math.sqrt(E_cm))
ASF=E_cm*cs*a
print(ASF)


Ecm=2908000
CS=float(input("Enter your value\n"))
ASF=Ecm*CS*math.exp(20.63/math.sqrt(Ecm))
print(ASF)


ASF=float(input("Enter your value\n"))
CS=float(input("Enter your value\n"))
CSE=float(input("Enter your value\n"))
ASFE=ASF*(CSE/CS)
print(ASFE)


ASF=float(input("Enter your value\n"))
E=float(input("Enter your value\n"))
PE= (-0.0097*(E**3))+(0.1908*(E**2))-(1.3719*(E))+11.975
print(math.log(ASF))
print(PE)


ASF=float(input("Enter your value\n"))
E=float(input("Enter your value\n"))
PE= (-0.1004*(E**4))+(3.1142*(E**3))-(35.85*(E**2))-(181.26*E)-330.11
print(math.log(ASF))
print(PE)


ASF=float(input("Enter your value\n"))
E=float(input("Enter your value\n"))
PE= (-0.1933*(E**4))+(6.1958*(E**3))-(73.88*(E**2))-(388.15*E)-748.49
print(math.log(ASF))
print(PE)
