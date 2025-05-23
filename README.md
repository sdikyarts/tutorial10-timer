## Experiment 1.2

### Add another print before spawn
![Print Before Spawn](print_before_spawn.png)

The println!("Yasmin's computer: hey hey"); is printed before the spawned async task because of the order of execution in the main function. When you call spawner.spawn(...), it schedules the async block (which prints "hola hola!" and "halo halo!") to run on the executor, but it does not execute it immediately. Instead, the main thread continues and immediately prints "hey hey" right after spawning the task. Only after this does the executor start running and process the queued async task, which then prints "hola hola!", waits for the timer, and finally prints "halo halo!". This demonstrates how spawning a task is non-blocking and allows the main thread to continue executing code right away.
