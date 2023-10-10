# FPGA-7-segment-decoder
The Truth Table:

![image](https://github.com/sidd2423/FPGA-7-segment-decoder/assets/112332747/a29db48f-f795-406e-859b-364433eb876f)

Minterms for the outputs: a(1,4,11,13)
b(5,6,11,12,14,15)
c(2,12,14,15)
d(1,4,7,10,15)
e(1,3,4,5,7,9)
f(1,2,3,7,13)
g(0,1,7,12)

Code:
module 7Segmentdecoder(sw0,sw1,sw2,sw3,a,b,c,d,e,f,g);
//define the switches  as inputs 
input sw0, sw1, sw2, sw3;
//define the outputs 
output a,b,c,d,e,f,g;
assign a = (~sw3 & ~sw2 & ~sw1 & sw0) | (~sw3 & sw2 & ~sw1 & ~sw0) | (sw3 & ~sw2 & sw1 & sw0) | (sw3 & sw2 & ~sw1 & sw0);
assign b = (~sw3 & sw2 & ~sw1 & sw0) | (sw2 & sw1 & ~sw0) | (sw3 & sw1 & sw0) | (sw3 & sw2 & ~sw0);



//Reduction (c) function: 
// In minterm form, the function was originally:
//c = (~sw3 & ~sw2 & sw1 & ~sw0) | (sw3 & sw2 & ~sw0) | (sw3 & sw2 & sw1);
// Reduction:
// Taking common terms and grouping:
//c = (~sw3 & ~sw2 & sw1 & ~sw0) | (sw3 & sw2 & ~sw0) | (sw3 & sw2 & sw1);
//= (~sw3 & ~sw2 & sw1 & ~sw0) | (sw3 & sw2 & (~sw0 + sw1));
// Now let's see if we can simplify further:
//c = (~sw3 & ~sw2 & sw1 & ~sw0) | (sw3 & sw2 & (~sw0 + sw1));
//assign c = (~sw3 & ~sw2 & sw1 & ~sw0) | (sw3 & sw2 & (~sw0 | sw1));


assign c = (~sw3 & ~sw2 & sw1 & ~sw0) | (sw3 & sw2 & ~sw0) | (sw3 & sw2 & sw1);
assign d = (~sw3 & ~sw2 & ~sw1 & sw0) | (~sw3 & sw2 & ~sw1 & ~sw0) | (sw2 & sw1 & sw0) | (sw3 & ~sw2 & sw1 & ~sw0);
assign e = (~sw3 & sw0) | (~sw3 & sw2 & ~sw1) | (~sw2 & ~sw1 & sw0);
assign f = (~sw3 & ~sw2 & sw0) | (~sw3 & ~sw2 & sw1) | (~sw3 & sw1 & sw0) | (sw3 & sw2 & ~sw1 & sw0);
assign g = (~sw3 & ~sw2 & ~sw1) | (~sw3 & sw2 & sw1 & sw0) | (sw3 & sw2 & ~sw1 & ~sw0);


endmodule


//part 2
module 7segmentdecoder2(sw, outputb);

input [3:0] sw;

output [6:0] outputb;

assign outputb[0] = (~sw[0] & ~sw[1] & ~sw[2] & sw[3]) | (~sw[0] & sw[1] & ~sw[2] & ~sw[3]) | (sw[0] & ~sw[1] & sw[2] & sw[3]) |  (sw[0] & sw[1] & ~sw[2] & sw[3]);

assign outputb[1] = (~sw[0] & sw[1] & ~sw[2] & sw[3]) | (sw[1] & sw[2] & ~sw[3]) | (sw[0] & sw[2] & sw[3]) | (sw[0] & sw[1] & ~sw[3]);

assign outputb[2] = (~sw[0] & ~sw[1] & sw[2] & ~sw[3]) | (sw[0] & sw[1] & ~sw[3]) | (sw[0] & sw[1] & sw[2]);

assign outputb[3] = (~sw[0] & ~sw[1] & ~sw[2] & sw[3]) | (~sw[0] & sw[1] & ~sw[2] & ~sw[3]) | (sw[1] & sw[2] & sw[3]) | (sw[0] & ~sw[1] & sw[2] & ~sw[3]);

assign outputb[4] = (~sw[0] & sw[3]) | (~sw[0] & sw[1] & ~sw[2]) | (~sw[1] & ~sw[2] & sw[3]);

assign outputb[5] = (~sw[0] & ~sw[1] & sw[3]) | (~sw[0] & ~sw[1] & sw[2]) | (~sw[0] & sw[2] & sw[3]) | (sw[0] & sw[1] & ~sw[2] & sw[3]);

assign outputb[6] = (~sw[0] & ~sw[1] & ~sw[2]) | (~sw[0] & sw[1] & sw[2] & sw[3]) | (sw[0] & sw[1] & ~sw[2] & ~sw[3]);

endmodule


Karnaugh Maps:
![image](https://github.com/sidd2423/FPGA-7-segment-decoder/assets/112332747/821f758a-54cf-4ae9-9822-f7b66e4727ce)

![image](https://github.com/sidd2423/FPGA-7-segment-decoder/assets/112332747/04d73ed4-1e63-46ef-b16a-39cbbbed1e90)



 

