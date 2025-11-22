# -Frequency-Modulation-and-Demodulation-using-NumPy-and-Matplotlib-

# __Aim:__

To implement and analyze frequency modulation (FM) using Python's NumPy and Matplotlib libraries.

# __Apparatus Required:__ 

1. Software: Python with NumPy and Matplotlib libraries
   
2. Hardware: Personal Computer

 
# __Theory:__

Frequency Modulation (FM) is a method of transmitting information over a carrier wave by varying its 
frequency in accordance with the amplitude of the input signal (message signal). The frequency of the carrier 
wave is varied according to the instantaneous amplitude of the message signal.

# __Algorithm:__

1. Initialize Parameters: Set the values for carrier frequency, message frequency, sampling frequency, and 
   frequency deviation.
   
2. Generate Time Axis: Create a time vector for the signal duration.
    
3. Generate Message Signal: Define the message signal as a cosine wave.
    
4. Compute the Integral of the Message Signal: Calculate the integral of the message signal over time.
    
5. Generate FM Signal: Apply the FM modulation formula to obtain the modulated signal.
 
6. Plot the Signals: Use Matplotlib to plot the message signal, carrier signal, and modulated signal.

# __Programme:__
```
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import hilbert

Fs = 5000 # Sampling frequency
Fc = 200 # Carrier frequency
f_mod = 20 # Modulating signal frequency
Am = 1.0 # Amplitude of the modulating signal
kf = 50 # Frequency deviation constant
t = np.arange(0, 1, 1/Fs)
modulating_signal = Am * np.cos(2 * np.pi * f_mod * t)
integral_of_message = np.cumsum(modulating_signal) / Fs
carrier = np.cos(2 * np.pi * Fc * t + 2 * np.pi * kf * integral_of_message)
plt.figure(figsize=(10, 8))

plt.subplot(3, 1, 1)
plt.plot(t, modulating_signal)
plt.title('Modulating Signal (Message)')
plt.xlabel('Time (s)')
plt.ylabel('Amplitude')

plt.subplot(3, 1, 2)
plt.plot(t, carrier)
plt.title('FM Modulated Signal')
plt.xlabel('Time (s)')
plt.ylabel('Amplitude')

analytic_signal = hilbert(carrier)
instantaneous_phase = np.unwrap(np.angle(analytic_signal))
instantaneous_frequency = np.diff(instantaneous_phase) * Fs / (2 * np.pi)

t_demod = t[1:]

plt.subplot(3, 1, 3)
plt.plot(t_demod, instantaneous_frequency - Fc) # Subtract carrier frequency
plt.title('Demodulated Signal (Recovered Message)')
plt.xlabel('Time (s)')
plt.ylabel('Frequency (Hz)')

plt.tight_layout()
plt.show()
```
# __Tabulation__:
<img width="1169" height="1280" alt="image" src="https://github.com/user-attachments/assets/943f5d15-2818-4341-88ec-30862f177aa9" />

# __Output:__
<img width="1097" height="820" alt="Screenshot 2025-11-17 205034" src="https://github.com/user-attachments/assets/105ad0cf-799a-49a8-8c1b-e3d4e6ad3541" />


# __Result:__

Thus the Frequency Modulation and Demodulation using NumPy and Matplotlib is verified successfully.
