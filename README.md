# brachistochrone_vpython
failed vpython 3d program for brachistochrone

Web VPython 3.2

g = 9.8
alpha = pi/4
s = sqrt(2)
sdot = 0
theta = pi/2
thetadot = 0
x3 = -1
x3dot = 0
R = 1
t = 0
dt = 0.01

while s>0:
  rate(50)
  sddot = -g*sin(alpha)
  thetaddot = -g*sin(theta)/R
  x3ddot = -(4*x3*x3dot**2-2*g*x3)/(1+4*x3**3)
  sdot = sdot + sddot*dt
  thetadot = thetadot + thetaddot*dt
  x3dot = x3dot + x3ddot*dt
  s = s + sdot*dt
  theta = theta + thetadot*dt 
  
  line1 = curve(pos = vec( -s*cos(alpha), s*sin(alpha), 0), color=color.green)
  line2 = curve(pos = vec(-R*sin(theta),  R*(1-cos(theta)), 0), color=color.blue)

  t = t + dt
 
  cyc_list = []

  while (theta <= 2*pi):
   y = x3**2
   x = x3 + x3dot*dt
  cyc_list.append(vector(x,y,0))
  cyc = curve(pos = cyc_list, color = color.red)

  
t = t + dt
print(sdot)
