# thread-safe-counter

I forked <https://github.com/jongchank/thread-safe-counter> as a public repository and modify it.

# The performance measurement result

## Semaphore

I compile tscounter.c as "semaphore".

![semaphore](https://user-images.githubusercontent.com/50652100/121805508-842a9800-cc86-11eb-8520-63d6c311ba5b.jpg)

Average: real 0m 6.643s
         user 0m 0.591s
         sys  0m 10.817s

## Mutex

I compile tscounter_original.c as "mutex".

![mutex](https://user-images.githubusercontent.com/50652100/121805519-8e4c9680-cc86-11eb-8e94-bb46567330f9.jpg)

Average: real 0m 0.018s
         user 0m 0.019s
         sys  0m 0.010s
         
# My analysis

The results showed that Mutex is much faster than Semaphore.

Implementation of semaphore is not complex but may consume more time than mutex
because the scope of the semaphore is larger(such as number of counts and waking up of other tasks).

In this case, it is better to use mutex than binary semaphore.

# OS environment

This code is compiled in WSL2.

### Department of Automobile and IT Convergence 20180991 Somyung Yun


