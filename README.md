# Design-of-FIR-Filters-using-rectangular-window
#          DESIGN OF LOW PASS FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of low pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM 
```
clc;
clear;
close;
N = 25;           
wc = 0.4 * %pi;    
alpha = (N - 1) / 2; 

hd = zeros(1, N);
for n = 0:N-1
    if (n - alpha) == 0 then
        hd(n+1) = wc / %pi;
    else
        hd(n+1) = sin(wc * (n - alpha)) / (%pi * (n - alpha));
    end
end

w = ones(1, N);

h = hd .* w;

Nfft = 1024;              
H = fft(h, -1);           
H = [H, zeros(1, Nfft - N)];
H = fft(H, -1);           

f = (0:Nfft-1) / Nfft;

plot(f, abs(H));
xlabel('Normalized Frequency');
ylabel('Magnitude');
title('Low Pass FIR Filter using Rectangular Window');
xgrid();

disp("Filter Coefficients:");
disp(h);
```

# OUTPUT
<img width="610" height="460" alt="image" src="https://github.com/user-attachments/assets/d516cef1-e1d8-4be3-9b6c-a7aec2ec5de6" />

# RESULT
The output waveform is verified
